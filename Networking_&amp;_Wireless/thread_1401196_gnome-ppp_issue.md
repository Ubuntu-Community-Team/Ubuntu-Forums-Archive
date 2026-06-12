---
title: "gnome-ppp issue"
date: 2010-02-07
forum: Networking &amp; Wireless
---

### Post by trevl on 2010-02-07
Hi all,

I have an issue with Gnome-PPP.

I have recently installed Ubuntu 9.10 on a Desktop PC. (Newbie to linux etc)
The PC is home-based, and is using a dial-up 56k connexn via external serial modem.
The machine is not on all the time, and also not on the net all the time. It has just the one user.

I have gone through all the forums advice and through other websites' advice.
I have got to the point where I have the external dial-up modem configured and working via wvdial, and also gnome-ppp - but only when running these apps as sudo through Terminal.

For example, when I do 'sudo gnome-ppp', from the Terminal, then the gnome-ppp GUI pops up, and I can make the connection from there.

BUT, when I do 'gnome-ppp' from the Terminal, (without sudo, and just as the root user) then the gnome-ppp GUI pops up, and when I try the same connection process, it gets stuck on sending password.

Same thing happens when I navigate via Applications (DropDownMenu) > Internet  > Gnome-PPP, then the gnome-ppp GUI pops up, I can *try* to connect, but the connection is stuck on sending password.

I have read of other users having a similar problem - 'stuck on sending password' when using dial-up, so I suspect I am not alone with this issue.

I *think* I have given all the necessary permissions to all the involved files and apps in the process.
Can someone tell me if this is a quirk of gnome-ppp, or is there yet one more file or app that needs su permission which I have not yet come across?
If the latter, can someone advise which it would be, or would likely be?

Thanks Trev
Australia

---

### Post by alexfish on 2010-02-07
hi

there is a thread here , but I don't know if it will help

please read all
[http://ubuntuforums.org/showthread.php?t=1369444](http://ubuntuforums.org/showthread.php?t=1369444)

regards

alexfish

---

### Post by _duncan_ on 2010-02-08
Need to add your user ID to the 'dip' group to use gnome-ppp without root privileges. The fastest way is to enter the following command in a terminal:
```
sudo adduser [COLOR="Blue"]userID[/COLOR] dip
```
replace [COLOR="Blue"]userID[/COLOR] with your actual user ID.
[B]
Log-out and then log back in[/B]. You should be able to connect using gnome-ppp without root privileges.

---

### Post by JPman on 2010-02-08
[B][QUOTE=trevl;8791421]Hi all,

I have an issue with Gnome-PPP.[/B]



Ubuntu stopped including wvdial with gui after 8.04 for some reason that no one has ever been able to discover.    This action by them seems rather cavalier and irrational.    Since then I've moved on to greener fields.

Ubuntu steadfastly ignores my requests for an explanation.    

My advice to you is to find another distro that still supports dialup.

JPman California  pissed at ubuntu

---

### Post by Bartender on 2010-02-08
This may not work for you very well, considering you're new to Linux, but if you want to try downloading Puppy Linux and installing it to a thumbdrive, I think that might answer some of your questions.  Puppy is a very lightweight distro, but that doesn't mean it's horribly geeky.  It's much more helpful than Ubuntu when it comes to dial-up.  I'm having problems with an internal hardware-based modem in Ubuntu.  Plug in the Puppy thumbdrive, I'm online in about one minute.
So this might work very well as a diagnostic tool for you.  If Puppy hangs at the same place as Ubuntu, then I'd be checking to make sure you've got the password entered correctly, etc.  If Puppy gets online, then you know it's something with Ubuntu or something in the way you set up gnome-ppp.

Another option - do you have a friend who's also on dial-up?  Maybe they'd let you use their username/password/phone # to try and connect to their ISP.  If you can get online with another ISP, that might help to diagnose the problem too.

Who's your ISP?

And what kind of external modem?

Actually, your problem sounds very similar to mine.  My internal US Robotics 5610 hardware modem appears to be locked up somehow inside of root permissions or groups or....  I can dial out using "sudo wvdial" and "sudo pon" but not "pon".  And gnome-ppp doesn't work at all ("Can't find modem on your system") until I first dial out with sudo wvdial or sudo pon.  THEN gnome-ppp works, but it's all lost as soon as I reboot.  

Thing is, I've never run into any sort of permissions problem with the external US Robotics 5686 modems.

---

### Post by trevl on 2010-02-08
>> Need to add your user ID to the 'dip' group to use gnome-ppp without root privileges.

The machine has no groups and no other users.
Do I need to first create a group called 'dip' or has this group already been created by one of the existing apps on-the-fly?

(The machine lives at another address and I dont get there every day, but, every week or so I visit. I try to leave it in a working condition when I do leave it alone - therefore like to be sure.)

Thanks 
Trev

---

### Post by alexfish on 2010-02-09
hi 

Re:                                  **[SIZE=2][COLOR=#000000][FONT=Georgia, Times New Roman, Times, serif][B]User Privileges- the dip and dialout groups**[/FONT][/COLOR][/SIZE][/B]

                                   [COLOR=#000000][FONT=Georgia, Times New Roman, Times, serif]On some versions of Ubuntu you do not automatically have all the permissions to run gnome-ppp if you are the first (default) user created even with though you should have all the normal administration privileges - you need to be both in the **dip **and the **dialout **groups to run it. This apparent mistake was probably done for additional security but is a nuisance. If this is the case the log file which is available from the Log button will have a line complaining about permissions for the executable file /usr/sbin/pppd.[/FONT][/COLOR]
  [COLOR=#000000][FONT=Georgia, Times New Roman, Times, serif]The easiest way to get the required privileges is to do System -> Administration -> Users and Groups then unlock with your password and highlight your user name and click Properties and on the User Privileges Tab tick 'Connect to Internet using a Modem' which adds you to the **dip **group and 'Use Modems' which adds you to the **dialout **group. Neither act immediately and you need to restart or logout and back in as the same user.[/FONT][/COLOR]
  [COLOR=#000000][FONT=Georgia, Times New Roman, Times, serif]If this does not work or you prefer to use a terminal then the following two commands will add YOURUSERNAME to the dip and dialup groups[/FONT][/COLOR]

  [COLOR=#000000][FONT=Courier New, Courier, mono][B]sudo adduser YOURUSERNAME dip
sudo adduser YOURUSERNAME dialout[/B][/FONT][/COLOR]

  [COLOR=#000000][FONT=Georgia, Times New Roman, Times, serif]You can check which groups you are in (and get some other useful information by:[/FONT][/COLOR]

  [COLOR=#000000][FONT=Courier New, Courier, mono]**id**[/FONT][/COLOR]
 
                                 **[COLOR=#000000][FONT=Georgia, Times New Roman, Times, serif][SIZE=3][B]Permissions for /etc/ppp/pap-secrets and etc/ppp/chap-secrets**[/SIZE][/FONT][/COLOR][/B]

  [COLOR=#000000][FONT=Georgia, Times New Roman, Times, serif]If you want to save the username and password in gnome-ppp they are saved in /etc/ppp/pap-secrets and etc/ppp/chap-secrets and you need to give read and write access to them from group dip - if you do not then you will get an warning message in the connection log. In most cases this does not matter as the username and password are not actually used or checked by most mobile internet providers - they know who you are from the SIM which is already registered before you can access data. Even so it is best to set these permissions. I use a root file browser which is started in a terminal by:[/FONT][/COLOR]

  [COLOR=#000000][FONT=Courier New, Courier, mono]**gksudo nautilus**[/FONT][/COLOR]

  [COLOR=#000000][FONT=Georgia, Times New Roman, Times, serif]You then navigate to folder /etc/ppp and right click on pap-secrets -> Properties -> Permissions tab then select dip from the drop down menu for Group and and then select read and write under Access. Repeat for chap-secrets. The annoying warning messages should now disappear.[/FONT][/COLOR]

  [COLOR=#000000][FONT=Georgia, Times New Roman, Times, serif]**Normal Configuration: **Once you have done the preliminaries above the main configuration is done by a GUI interface and is all fairly obvious if you are making a simple land-line Dial-Up connection. The default modem initialisation strings and other settings will almost certainly work so only the initial screen needs the username, password and telephone number need setting for a simple land-line modem. You may have to set the device for your modem by clicking settings if it is a none standard types of modem. The only thing missing with gnome-ppp is help. It uses its own configuration file $HOME/.wvdial.conf which it is reported can have additions despite the warnings not to modify by hand. [/FONT][/COLOR] 

 Also check the admin users and groups for a modem ; if you see a modem listed then check the permissions 

Hope this is of some help : also will give you an insight of how gnome ppp works

The above is from

[http://www.pcurtis.com/ubuntu-mobile.htm](http://www.pcurtis.com/ubuntu-mobile.htm)

---

### Post by _duncan_ on 2010-02-09
> **trevl said:**
> >> Need to add your user ID to the 'dip' group to use gnome-ppp without root privileges.

The machine has no groups and no other users.
Do I need to first create a group called 'dip' or has this group already been created by one of the existing apps on-the-fly?

(The machine lives at another address and I dont get there every day, but, every week or so I visit. I try to leave it in a working condition when I do leave it alone - therefore like to be sure.)

Thanks 
Trev

No need to create the dip group. It's created by default.

---

### Post by trevl on 2010-03-12
Hi all,

It's all sorted. Now dialing up via Gnome-ppp.
ALL the things which were advised here and elsewhere, were done. Everything.
papsecrets, chapsecrets, user in dialout and dip groups. I gave the user admin rights to every item I touched.

The only thing I can think of, is that some of the process might be sequence critical.
Or, that when the processes were completed, then the system didn't initiate them straight away.
A bit odd. I did the whole thing twice - starting from fresh install of Ubuntu 9.10.
Checked the status of each file as I went along. 
When I was still dialing up via sudo, then I wrote my initial query.

I wrote everything down, and might re-visit my notes to transcribe to a webpage for others.
Notes and advice to pieces of the process tend to be all over the place, so its a bit of fiddling.
It's a mystery why the necessary software for dial-up wasn't pre-loaded with the OS install. 
Maybe the dial-up components are not currently reliable enough to be included in an OS release? Who knows.

Thanks all, 
Trev 
Australia

---

