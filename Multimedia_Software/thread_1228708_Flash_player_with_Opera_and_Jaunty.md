---
title: "Flash player with Opera and Jaunty"
date: 2009-08-01
forum: Multimedia Software
---

### Post by fatdadkev on 2009-08-01
There are several discussions about Flash not working with Jaunty (9.04) and Opera so I hope this helps anyone struggling or stuck in a loop.

I've two identical laptops, one it works fine on (Opera was installed before the upgrade from 8.10 and the other was upgraded from 8.10 to 9.04).
Let's call them Laptop A and B - With A Flash works fine in Opera and works smoother than Flash with Firefox.

Both have "flashplugin-installer" installed through package manager and I even tried installing flash directly from adobe itself i.e they both have the same flash player installed but flash works fine on Laptop A with Firefox AND Opera, it only works on Firefox on laptop B.

If you go to Opera and download the debian package i.e the official opera install (Opera 9.64) you will find Flash still does not work.
If you check URL "[opera:plugins]("opera:plugins")" you may find "libflashplayer.so" is showing correctly in "/usr/lib/opera/plugins/libflashplayer.so" (or /usr/lib/flashplugin-installer/libflashplayer.so) but still nothing plays in Opera - there are many posts for redirecting the Opera links to the Mozilla plugin directory etc but these still don't appear to work.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=123181&stc=1&d=1249123954[/IMG]

The solution appears to be what version of opera you install.
If you go to Operas web page and download the deb install package this installs "**opera-static**" (look for Opera in package manager and it will confirm opera-static is installed).

Checking Laptop A I find this is running **Opera** not ***Opera-static*** so using the package manager I completely removed opera-static from laptop B (remember to **COMPLETELY** remove including configuration files)

Edit your sources list from a terminal window 
**sudo gedit /etc/apt/sources.list **
Put in an entry for Opera (the first line below is just a comment line to help you remember what the entry is).

[B]# Opera
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) lenny non-free[/B]

Now save and exit the file
Import the gpg key or you will get an error when trying to update your software sources.

In terminal type
**sudo wget -O - [http://deb.opera.com/archive.key](http://deb.opera.com/archive.key) | sudo apt-key add -**

This should import the key with an OK message.
Refresh your software sources/list
[B]
Sudo apt-get update [/B]

Now check your package manager and look for "opera" you should notice TWO versions now, opera and opera-static.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=123180&stc=1&d=1249123021[/IMG]

Install opera (NOT the static version or you will be back to square one).

This now works fine on laptop B.

if you have any problems with the gpg key or the source URL then go to [http://deb.opera.com](http://deb.opera.com) which has all the URL and key locations.

To confirm flash is working go to
**[http://www.adobe.com/shockwave/welcome/](http://www.adobe.com/shockwave/welcome/)**
you should see a confirmation graphic for Adobe Flash Player.

Note you don't see a confirmation for Adobe Shockwave player when you test it on the page above, don't worry about that - this is just to get Flash working - we like playing Flash games ([http://armorgames.com/](http://armorgames.com/)) and although I use Firefox as my primary browser I find Flash is smoother and does not show any screen interference on opera (I suspect my screenlets, pidgin etc are being refreshed with my auto wallpaper changer which upsets Firefox but Opera seems immune to these problems).

Hope this helps anyone with this problem, after hours of trial and error these steps take about 3 minutes and worked first time.
I have also tested that you can change the plugin location within Opera to Flash or even the flash alternative or different locations, they all work i.e it's not an issue if your pointing to an alternative plugin location as long as it works (I've pointed mine to /usr/lib/flashplugin-installer/libflashplayer.so) 

I appreciate comments etc as I know I struggled for a while with this before reaching this conclusion.

---

### Post by timjohn7 on 2009-08-01
Does this fix work with Opera 10 Beta 2?
I have Flash working after a fashion, but have to "Download and activate this control" for each incident of Flash on each website that I visit.

---

### Post by Arup on 2009-08-01
Never had any issues with any version of Flash in Jaunty, only in Kubuntu I had to install qt3-libs. All I do is put libflashplaeyr.so in /usr/lib/mozilla/plugin and Opera 9x or 10x picks it up fine. I have used it on Opera 9.xx qt3 build and now using it on Opera 10 beta qt4.

---

### Post by dilb on 2009-08-03
Worked great for me, thanks very much!

---

### Post by aflog on 2009-08-03
Thank you thank you so much!

I'm sick of using firefox for flash things, firefox is too slow. Opera ftw :P Worked perfectly.

---

### Post by Fake Dog on 2009-08-04
Awesome, thank you very much!

One strange thing, when I searched for "opera" in Synaptic, only opera-static showed up. But if you scroll down on the opening page with all the software, opera is there. Just in case that might have confused anyone else!

---

### Post by squashpup on 2009-08-10
Thanks for the help, one and all.

A (perhaps) simpler method for newbies to do the same thing:

Go to this link:

[http://www.opera.com/browser/download/?os=linux-i386&list=all](http://www.opera.com/browser/download/?os=linux-i386&list=all)

Click on "Opera 9.64".  It will take you to a download page.

In the drop-down box, choose Debian. Make sure the first option (Debian 5.0) is checked. Click the green "Download Opera" button.  Save where you can find it.

Now, close your browser, open a terminal and type "sudo apt-get remove opera"

When it finishes, find the file you downloaded before and double click.  Opera will install.

This does the same thing as above, but doesn't require you to mess with repositories.

---

### Post by niikos on 2009-08-19
hello I have followed the instructions above, the youtube are playing but dropping a lot of frames. using the top command I see that the operapluginwrap is using a lot of the cpu (over 65%). I have tried to disable/enable hardware acceleration, but nothing. If I download the youtube videos they are played good. I am using ubuntu 9.04 and my pc is a Toshiba S2400-103 with 512MB ram and an S3 SuperSavage/IXC AGP 4x Graphic card.

The youtube videos were played fine before formating in a Windows XP and openSUSE 10.3 OS.

---

### Post by souteneur3190 on 2009-08-19
YOU ARE A GENIUS! thank you, i know you completed a lot of "perfect" desktops out there with that fix...firefox is just too slow in everything.

---

### Post by king EZi on 2009-08-22
Thanks...youtube is working now...although i still have a problem with apple trailers, would be glad to get help with that.

---

