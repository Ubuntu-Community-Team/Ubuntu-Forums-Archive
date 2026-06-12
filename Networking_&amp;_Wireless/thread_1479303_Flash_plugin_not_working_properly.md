---
title: "Flash plugin not working properly"
date: 2010-05-10
forum: Networking &amp; Wireless
---

### Post by Sciamano on 2010-05-10
Hello!
It's been a few hours since the Adobe Flash plugin on my Firefox is behaving in a strange way: some of the clickable dialogs do not work anymore. I click on them but nothing happens.

For example: in chatroulette, the dialog that asks for the permission to use the webcam can't be clicked:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=156347&stc=1&d=1273518078[/IMG]

Same happens for other flash sites.
I'm using Firefox "Namoroka" v3.6.5pre and Flash 10.0r45

:confused:

Anyone else experiencing this?

Thanks
Luca

---

### Post by md1111 on 2010-05-10
Me too. And it eats up my resources - CPU & RAM. I don't know?? I'm thinking of reinstalling the flash plugin for Namoroka.

---

### Post by guyholland on 2010-05-10
I had this exact issue. I removed all versions of flash and reinstalled the newest version from Adobe's site. I forget how I did it but the guide on youtube was called 'Adobe Flash x64 Ubuntu 10.04 How-To'.

This may help. Good luck.

---

### Post by md1111 on 2010-05-10
Found a solution. A quick reinstall is going to fix it. Found a post on some forum and this is how it worked for me.

1. Go to Adobe for the latest version and download .deb

2. Copy this text into text editor and shutdown all browsers (for future reference :-) ).

3. Use Synaptec to remove flash or paste the line to terminal (I used Synaptec because at first it didn't find me Flash installed while running this in terminal)[FONT=Verdana]
[/FONT]sudo apt-get remove flashplugin-nonfree 

4. Run this
sudo dpkg -i install_flash_player_10_linux.deb

5. Start your browser and everything should work just fine. Best regards.

---

### Post by Sciamano on 2010-05-11
Good to know in case this problem presents itself again.
The fact is that mine has spontaneously started working again. :confused:

---

### Post by BlacqWolf on 2010-05-11
[http://usefulsoftwaregamesandknowledge.blogspot.com/2009/09/install-and-run-64-bit-flash-on-linux.html](http://usefulsoftwaregamesandknowledge.blogspot.com/2009/09/install-and-run-64-bit-flash-on-linux.html)

this may help....

i found a post earlier when i was using x64 with x86 flash, and it worked much better, but i cannot seem to find it anymore :confused:

and, flash sometimes likes to pull tricks and temporarily work, and then stop again. i had this done to me many times before...

---

