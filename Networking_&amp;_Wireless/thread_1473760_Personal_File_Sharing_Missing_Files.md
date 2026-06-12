---
title: "Personal File Sharing Missing Files"
date: 2010-05-05
forum: Networking &amp; Wireless
---

### Post by Throne777 on 2010-05-05
(Running Lucid Lynx) In the Personal File Sharing Preferences it won't let me to tick the box to share public files on the network as it says the required packages are not installed on my system. 
The options for sharing via Bluetooth are available to me however. 
What packages am I missing (and how do I get hold of them)?

Thanks.

---

### Post by kwalters on 2010-05-06
This is a known bug which has been reported several times.

You need to install the following

Apache2.2.bin
lib-apache2-mod-dnssd

You can use the synaptic package manager (click on System then Synaptic Package Manager)  There is a search function there and if you insert <apache> all the required modules will appear (the second is quite a long way down and I nearly gave up)

Once they are installed, the function will no longer be greyed out

---

### Post by DigitalMage on 2010-05-06
> lib-apache2-mod-dnssd

It showed up as libapache2-mod-dnssd for me.  Not sure if that will assist people in their search.

---

### Post by dannyboy79 on 2010-05-06
> **kwalters said:**
> This is a known bug which has been reported several times.

You need to install the following

Apache2.2.bin
lib-apache2-mod-dnssd

You can use the synaptic package manager (click on System then Synaptic Package Manager)  There is a search function there and if you insert <apache> all the required modules will appear (the second is quite a long way down and I nearly gave up)

Once they are installed, the function will no longer be greyed out

what exactly does this "personal file sharing" option mean? if it's installing apache stuff, is it sharing them via the web? i already have samba installed and although I am comfortable manually editing smb.conf, i wanted to check this out but was also presented with option greyed out. can someone explain why the 2 extra libs/apps are required for "personal file sharing" to work?

---

### Post by Morbius1 on 2010-05-06
dannyboy79, 

I had the same thought's as you. It's confusing enough for the new user that there are two ways already to share folders: Nautilus-share and Classic-share. Now they add this - and it requires apache?

I'm still in the discovery process myself on this but it appears the package in question is : **gnome-user-share** ( which is already an unfortunate name because it resembles usershare in Nautilus-share )

Here's the description in synaptic:
> gnome-user-share is a small package that allows easy user-level file sharing
via WebDAV or ObexFTP. The shared files are announced on the network by Avahi Not sure how one connects WebDAV and Avahi but since windows has a webdav client and there is no avahi ( or bonjour on windows ) by default on windows it's a little confusing to me.

Should work like a charm between ubuntu's and between ubuntu and OSX though.

---

### Post by dannyboy79 on 2010-05-07
well from what I know of webdav it can be used for file sharing via http. like once i jailbroke my iphone, theres an app in cydia that makes in webdav capable so i can login to it from firefox after i installed webfolder. iphone can be connected via usb cord or on my internal wifi network. I dont' really see the advantage of this when you have to use firefox or other webdav client. why not just use trusty samba? is this share thing by default not listening to requests outside your internal network????? that's the main security question.

---

### Post by Morbius1 on 2010-05-07
I downloaded the source for this thing so I can read the README:

> gnome-user-share is a small package that binds together various free
software projects [COLOR=Blue]to bring easy to use user-level file sharing to the
masses[/COLOR].

The program is meant to run in the background when the user is logged
in, and when file sharing is enabled [COLOR=Black]a webdav server is started that
shares the $HOME/Public folder[/COLOR]. The share is then published to all
computers on the local network using mDNS/rendezvous, so that it shows
up in the Network location in Gnome.

The dav server used is apache, so you need that installed. Avahi or 
Howl is used for mDNS support, so you need to have that installed and
mDNSResolver running.First, I though Nautilus-share brought user-level file sharing to the masses.

It's only sharing the Public folder in your home directory.

It's still not clear if all the clients need to have mDNS, rendezvous, avahi, bonjour, or whatever it's called at the moment.  ( BTW, never heard of Howl before. ) 

I guess I'll just have to try it --- someday.

---

### Post by dannyboy79 on 2010-05-07
> **Morbius1 said:**
> First, I though Nautilus-share brought user-level file sharing to the masses.

Nautilus-Share uses samba as a backend, gnome-user-share uses apache to serve the files over webdav.

---

### Post by Morbius1 on 2010-05-07
> Nautilus-Share uses samba as a backend, gnome-user-share uses apache to serve the files over webdav.     Yes, but by default nautilus-share allows users to share any directory they own without becoming root. And nothing can be simpler than right clicking on a folder and selecting "Share this thing" ( I'm paraphrasing ;) ).

I think that above description qualifies as bringing "user-level file sharing to the masses". :p

---

### Post by untmdsprt on 2010-05-08
> **Morbius1 said:**
> Should work like a charm between ubuntu's and between ubuntu and OSX though.

Both computers can see each other, but only the Ubuntu PC can access the Mac's folders. The Mac keeps giving me an error of "The operation can't be completed because the original item can't be found." Anything else I need to set on the PC so the Mac can access everything?

---

### Post by dannyboy79 on 2010-05-10
> **untmdsprt said:**
> Both computers can see each other, but only the Ubuntu PC can access the Mac's folders. The Mac keeps giving me an error of "The operation can't be completed because the original item can't be found." Anything else I need to set on the PC so the Mac can access everything?
so you trying to access files on ubuntu from mac right? are the users account the same name, paswords the same? if not, you could try to create a username.map file on your ubuntu machine to map a user on the mac to the user on ubuntu. 
Example:
I have a user named bill on my win 7 computer but a user name ted on ubuntu. within ubuntu's smb.conf I specify this:
username map = /etc/samba/username.map
and then this is the persmissions of that file on ubuntu:
-rw-r--r--   1 root root   157 2010-05-03 17:46 username.map
and within that file I have this
ted = bill
and then when bill tries to log in from teh mac, it will map that name to ted's account and you'll need to use ted smb password to login to a share. Good luck

---

### Post by Morbius1 on 2010-05-10
dannyboy79,[I][B]

Personal File Sharing[/B][/I] doesn't use a username only a password. Remember this isn't samba.

It sort of looks like the old "share level" security that samba had in days gone by.

---

### Post by Morbius1 on 2010-05-10
I've been playing with this the last few days and I think I now understand why it's greyed out by default. It doesn't work very well.

I can't get a Windows client to access it at all although I really didn't try very hard. As for a linux client - sometimes it works flawlessly, most of the time you'll get the following error:
> DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)Click on the icon in Nautilus again and your fine. The next minute you get some HTTP Error.

On the whole I think I'll stick with samba. :wink:

---

### Post by zdamp on 2010-05-14
please delete this post

---

### Post by rg_stephens on 2010-05-24
Ok, I installed the missing modules. I can now share files between my two Ubuntu computers:P But if I try to open a OpenOffice.org file across the network, I get a *General I/O Error*. My excitement over networking has fallen a few notches....

I have my hopes up that one day Ubuntu (or someone) will make networking simpler. I've spent too many hours trying to set up a simple LAN that just works.

---

### Post by msimon1960 on 2010-06-19
> **kwalters said:**
> This is a known bug which has been reported several times.

You need to install the following

Apache2.2.bin
lib-apache2-mod-dnssd

You can use the synaptic package manager (click on System then Synaptic Package Manager)  There is a search function there and if you insert <apache> all the required modules will appear (the second is quite a long way down and I nearly gave up)

Once they are installed, the function will no longer be greyed out

This worked for me!

Someone should update the help file for 'personal file sharing' with this information.  The information currently provided is inaccurate and obtuse.

---

### Post by Jimmyfj on 2010-09-27
> **rg_stephens said:**
> Ok, I installed the missing modules. I can now share files between my two Ubuntu computers:P But if I try to open a OpenOffice.org file across the network, I get a *General I/O Error*. My excitement over networking has fallen a few notches....

I have my hopes up that one day Ubuntu (or someone) will make networking simpler. I've spent too many hours trying to set up a simple LAN that just works.

Don't give up on yourself just yet. Networking isn't that hard once you learn how to use it. Only if you haven't tried networking before, or read some stuff about it it can cause you a headache. 

Reading my way through this thread I wanted to see if things really has become that bad? They haven't - If you want simple and easy to manage networking Linux <> Windows use the Nautilus File Sharing. It works, and it uses Samba. It took me less than 3 min to get my share up and running just by installing the Nautilus File Share Packages, which by the way was very easy. Right click on a folder you want to share. Select "Share this folder" and click Install Packages. The rest is a walk in the park.

Here's a little something on networking:

[aboutdebian.com/network.htm]("http://www.aboutdebian.com/network.htm")

---

