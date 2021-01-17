<h2 align="center">Bash Scripting Cheatsheet with some highly practical examples</h2>

<br>

##### Bash Script Variables

```bash

greeting="Hello"
 
echo $greeting

```

#### User input

```bash
echo "enter your text :"
	
read  DATA

```
> _now we can use this as a globlal variable $DATA_


> _another way_

```bash
read -p "Enter your name: " name
```
> _now we can use this as a globlal variable $name_




#### if statement

```bash
if [ "example1" = "example2" ]; then
  echo "matches"
else
  echo "doesn't match"
fi
```

> _An example of if statement_

```bash
a="10"

b="10"


if [ "$a" == "$b" ]; then

  sudo apt update && sudo apt upgrade

else

  echo "doesn't match"

fi
```

#### comparison operators

```bash
word1="Hello"
word2="Hello"
word3="hello"

 
if [ $word1 == $word2 ] 
then
  echo "Strings are equal"
fi
 
if [ $word1 != $word3 ]
then
  echo "Strings are not equal"
fi
```

#### Pipes

```bash

a > file.txt 
```
> _save output of command a into file.txt (overwrite)_

```bash
a >> file.txt 
```
> _save output of command a into file.txt (append)_
```bash
command1 ; command2 
```
> _command2 will be executed after command1_

> _which is the same as_

```bash
command1
command2
```
```bash
command1 && command2 
```
> _command2 will be executed if, and only if, command1 finishes successfully (returns 0 exit status)_

```bash
command1 || command2 
```

> _command2 will be executed if, and only if, command1 finishes unsuccessfully (returns code of error)_



#### function

```bash
function_name() {
    shell commands
}
```
> _call as function_name_


> _An example for function_

```bash
push() {
  
   echo "commit message: " 

   read msg 
   
   git status

   git add -A

   git commit -m "$msg"

   git push
}
```

#### Case statement

```bash
case "$1" in
  start | up)
    vagrant up
    ;;

  *)
    echo "Usage: $0 {start|stop|ssh}"
    ;;
esac
```


> _An example menu with case statement_

```bash
x=0
while [[ $x == 0 ]]

do
	clear
        echo "Select a number to install 1-dwm, 2-bspwm, 3-media suite(obs, kdenlive, gimp, virtualbox) ? (1/2/3)"
	read answer
	
	case "$answer" in 

 		1)
 		cd .. && git clone https://github.com/yperta/dwm-dots
          cd dwm-dots && chmod +x ./vm-setup.sh && sh vm-setup.sh
		x=1
		;;
		2)
		cd .. && git clone https://github.com/yperta/bspwm
    cd bspwm && chmod +x ./vm-setup.sh && sh vm-setup.sh
		x=1
		;;
		3)
		sudo pacman -S obs-studio gimp virtualbox --needed --noconfirm
    cd .. && git clone https://aur.archlinux.org/yay-bin.git && cd yay-bin && makepkg -si --noconfirm
    yay -S virtualbox-ext-oracle --needed --noconfirm     
	    x=1
		;;
    *)
    printf "\nInvalid Option" & sleep 3 && exit 0
    ;;
		

	esac	
done
```

#### Heredoc

```bash

cat <<EOF
text1
one
text2
hello world
two
text3
EOF
```

#### An example for Heredoc

```bash
cat > hello.py << EOF                                                                          
#!/usr/bin/env python
from __future__ import print_function
import sys
print("#stdout", file=sys.stdout)
print("#stderr", file=sys.stderr)
for line in sys.stdin:
print(line, file=sys.stdout)
EOF
```

> _Example 2_

```bash
bash << EOF
sudo apt update || sudo apt autoremove
EOF
```

>_Example 3_

```bash
cat - <<EOF > /etc/profile.d/socksproxy.sh
#!/bin/sh
export SOCKS_PROXY="socks5://127.0.0.1:9050"
EOF
```

#### sed

```bash
sed 's/Nick/John/g' report.txt 
```

>_Replace every occurrence of Nick with John in report.txt_

```bash
sed 's/Nick|nick/John/g' report.txt 
```
>_Replace every occurrence of Nick or nick with John._

```bash
sed '$d' file.txt 
```
>_Delete the last line_

```bash
sed '/boom/!s/aaa/bb/' file.txt 
```
>_Unless boom is found replace aaa with bb_

```bash
sed '17,/disk/d' file.txt 
```
>_Delete all lines from line 17 to 'disk'_

```bash
sed '1,20 s/Johnson/White/g' file.txt 
```

>_Do replacement of Johnson with White only on lines between 1 and 20_

```bash
sed '/OS/d' os.txt 
```
>_Delete those lines from os.txt file that contains the text, ‘OS’._








