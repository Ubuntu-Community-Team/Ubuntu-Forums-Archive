---
title: "How to see what happens when usb inserted"
date: 2011-06-26
forum: Networking &amp; Wireless
---

### Post by odius on 2011-06-26
HI. I know its out there somewhere but I think I will need further help so here it is...

I want to connect my new Blackberry Playbook to Ubuntu via the usb cable. So what I have done, whether or not I needed to, was install samba4 and nfs. Long Long story short I have figured that if I connect in the playbook, restart it then I get two different networking applet options. Auto Eth0  and Auto Ethernet.  I'm tireed right now and I know usb works with the auto eth0 not entirely sure about the wireless although i think it was working....


So..... what I want to find out is why do I need to restart the playbook in order for the os to use it?
There is a tail command but will this be enough to tell if it is installing a driver and if it is how can it be made permanent?  Soo many questions.....

Oh I go to File in nautilus and select connect to server, smb://playbook

thanks

---

### Post by michael-buehner on 2011-12-28
Simple!
 
On the Blackberry Playbook
 
1) Go to SETTINGS > USB CONNECTIONS >
    Select - CONNECT TO WINDOWS
    Select - FILE SHARING - ON
    Select - PASSWORD PROTECT - OFF (you can enable, but for this easy purpose, leave off)

2) Go to SETTINGS > ABOUT > NETWORK
     Write down the USB IPv4 ADDRESS
3) Connect the Playbook with the USB Cable
 
On your Ubuntu PC
 
1) Go to PLACES > CONNECT TO SERVER
2) Select TYPE > WINDOWS SHARE
2) SERVER IP - Type in the Playbook USB IPv4 ADDRESS
3) Select CONNECT
 
You should see all of the folders (Music, Videos, Photos, Print, etc......)
 
Drag and Drop to your hearts content!
 
When you are finished, simply TURN OFF FILE SHARING unless you have used a password
 
 
Hope this helps!


:D

---

### Post by Fraoch on 2012-01-03
I suspect a few Ubuntu users found a PlayBook under the Christmas tree this year due to the sale at the end of November, although I see that post-Christmas sales match those prices too.

Michael's little tutorial works perfectly, but:

- you have to do this every time you connect via USB because the USB IP address changes every time

- obviously michael's experience is different but I had to set PlayBook's settings - USB connections as "Connect to Mac" in order to get it to connect to Ubuntu over USB

- it's a similar procedure for wireless BUT since the wireless IP doesn't change, it persists between reboots of both the Ubuntu machine and the PlayBook

If you do file sharing over wireless make sure to turn on password protection as anyone could just come in, read, alter and delete files.  File sharing over wireless is even available when the unit is in standby, so turn password protection on if you turn wireless sharing on.

Also note that the PlayBook's network share is easily visible to Ubuntu but *don't use it*.  It never seems to work, always timing out with a "failed to retrieve share list from server" error.  You must follow Michael's tutorial and map it as a server at an IP address.

---

