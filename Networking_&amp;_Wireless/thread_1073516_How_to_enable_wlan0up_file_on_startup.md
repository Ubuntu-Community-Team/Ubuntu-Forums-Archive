---
title: "How to enable wlan0up file on startup?"
date: 2009-02-18
forum: Networking &amp; Wireless
---

### Post by MG101 on 2009-02-18
Hello fellas,

Every time I reboot or start my computer (dual boot) in order to get wireless I have to run Nautilus and then double click on a file called wlan0up in order to start the wireless. That file is inside a folder with some drivers I had to recompile to get my wireless working.

Anyway, is there anyway to automate this process on startup so that I don't have to double click on the file with Nautilus every time? I guess I want that wlan0up file activated on startup or something.

Thanks guys.

---

### Post by superprash2003 on 2009-02-18
is it an sh file?? if so , just add it as a task and enter the command as sh filename and put that file in your home folder [http://www.prash-babu.com/2008/11/how-to-launch-application-or-command.html](http://www.prash-babu.com/2008/11/how-to-launch-application-or-command.html)

---

### Post by MG101 on 2009-02-18
I apologize for not mentioning it. I right-clicked on the file and it says shell script, so I guess it is an ss file. In any case, I tried that and it didn't work. Maybe because I can only double click on it when Nautilus is open (which requires administrator privileges).

The link you gave me does have a workaround, but it includes typing the password there and I really hope I don't have to leave my password out there in the open.

The file is at this address:
/root/rtl8187se_linux_26.1023.0928.2008/wlan0up

Do you have any other ideas? 

Thank you!

---

### Post by vandorjw on 2009-02-23
1.
cd /root/rtl8187se_linux_26.1023.0928.2008    **enter**
sudo cp wlan0up /usr/sbin                     **enter**
sudo update-rc.d wlan0up multiuser            **enter**
type password

however, I am not 100% sure on this method.

2.
open your .bashrc file using "gedit .bashrc"
add this line to the bottom.
> 
alias wireless="/root/rtl8187se_linux_26.1023.0928.2008/wlan0up"


what this does is, whenever you open the terminal and type "wireless" , bash (the default shell language) will recognize this as a command to run the specified file.

Once again, I didn't fully research this yet, but I find this easier than browsing to the file and clicking it.

(I wonder, what happens when you display the file...is is readable??) or does it display boxes?


3.
Keep playing around with sessions

You have probably already tried this, but as the command, input
/root/rtl8187se_linux_26.1023.0928.2008/wlan0up

if you need root privalleges, I think you can put 

sudo /root/rtl8187se_linux_26.1023.0928.2008/wlan0up

-------------------------------------------------------------


Good luck, I will look into it a bit more.

If it is a shell script file, then please post what it says.

Cheers and Goodnight.
CC7

---

