---
title: "[SOLVED] Shell Script on OSX"
date: 2008-12-16
forum: Mac OSX
---

### Post by linuxguymarshall on 2008-12-16
I just wrote a shell script but I do not have Linux with me. Only OS X. Any idea how to run it. I have tried everything I can think of.

---

### Post by handydan918 on 2008-12-16
> **linuxguymarshall said:**
> I just wrote a shell script but I do not have Linux with me. Only OS X. Any idea how to run it. I have tried everything I can think of.

And what exactly have you thought of? Perhaps a look at the script would help, as well.

---

### Post by linuxguymarshall on 2008-12-16
I know the script is fine. It runs perfectly on Linux (tested on ubuntu, fedora, red hat, suse, and damn small) but it returns this on osx when I run the following command :

```
sh bob.sh
```

returns this 

```
bob.sh: line 1: syntax error near unexpected token `newline'
bob.sh: line 1: `<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TR/html4/strict.dtd">'
```

---

### Post by schauerlich on 2008-12-16
It would be useful to see the script, although it looks like your script is an HTML file...

EDIT: Does your script use wget? Because OS X doesn't have wget. It can be installed via MacPorts though. The BSD and GNU coreutils are different.

---

### Post by linuxguymarshall on 2008-12-16
Yeah. Then HTML error was what really intrigued me. 

Here is the script

```

#!/bin/bash/
clear
echo "Testing "
sleep 5
clear
echo "Please type your password so the program can gain full access"
sudo gainroot
clear
echo "Setting up test files / moving to them"
mkdir ~/.testfiles/
mkdir ~/.testfiles/tmp
mkdir ~/.testfiles/prgrms
mkdir ~/.testfiles/prgrms/games
mkdir ~/.testfiles/prgrms/utils
mkdir ~/.testfiles/prgrms/prod
mkdir ~/.testfiles/prgrms/art
mkdir ~/.testfiles/prgrms/media
mkdir ~/.testfiles/prgrms/media/edit
mkdir ~/.testfiles/settings
mkdir ~/.testfiles/lam/menus/
mkdir ~/.testfiles/lam/
mkdir ~/.testfiles/lam/scripts
mkdir   ~/.testfiles/lam/scripts/other/
cd ~/.testfiles/
clear
echo "test"
echo "----------------------- "
echo "Please choose an option"
echo "test ---------- 1"
echo "test ----------  2"
echo "test ---------- 3"
echo "About test ---------- 4"
echo "Please choose an option"
read menuop1
if [ $menuop1 -eq 1 ] ; then
~/.testfiles/lam/menus/1.sh

else
 if [ $menuop1 -eq 2 ] ; then
   ~/.testfiles/lam/menus/2.sh
else
 if [ $menuop1 -eq 3 ] ; then
  ~/.testfiles/lam/menus/3.sh
else
 if [ $menuop1 -eq 4 ] ; then
   ~/.testfiles/lam/scripts/other/4.sh
else
echo "That is not an option"
sleep 3
echo "closing in  5"
sleep 1
clear
echo "closing in  4"
sleep 1
clear
echo "closing in  3"
sleep 1
clear
echo "closing in  2"
sleep 1
clear
echo "closing in  1"
clear
exit
fi
fi
fi
fi

```

---

### Post by schauerlich on 2008-12-16
Did you write the script from a linux machine? I've had trouble before with Linux and OS X having different conventions for whitespace, and if it's complaining about newline, that might be it. Just a guess.

---

### Post by linuxguymarshall on 2008-12-16
I started writing it in VIM on OS X, did a bit of editing on Windows (With VIM) and then did what you see now in VIM on OS X

---

### Post by schauerlich on 2008-12-16
Your script works fine on OS X for me. Not sure what to tell you.

---

### Post by linuxguymarshall on 2008-12-16
> **EDavidBurg said:**
> Your script works fine on OS X for me. Not sure what to tell you.


What version of OS X are you using. What command?

Im on Version 10.4.11 (Tiger)

---

### Post by schauerlich on 2008-12-16
I'm on 10.5.6. Try pasting the script from your post above into a new text file in textedit, save it as plain text and try it. Format > Make Plain Text

---

### Post by linuxguymarshall on 2008-12-16
What command did you run.

---

### Post by schauerlich on 2008-12-16
> **linuxguymarshall said:**
> What command did you run.

I saved it as ~/foo.sh and ran
```
sh foo.sh
```

---

### Post by linuxguymarshall on 2008-12-16
Magical, it works now

---

### Post by linuxguymarshall on 2008-12-16
Ah, I figured it out

I think somewhere along the way it got mixed up with an HTML file as it has a lot of HTML formatting. I recompiled in VI and that was what fixed it.

---

### Post by schauerlich on 2008-12-16
Yeah, I figured it was something like that. glad it's working now.

---

