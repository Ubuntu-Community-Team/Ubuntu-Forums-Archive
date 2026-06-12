---
title: "Shared Folders over local network possible?"
date: 2010-09-17
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by andrewabc on 2010-09-17
Ok, so I have two computers in house. 1 upstairs directly connected via ethernet cord to router. Other is downstairs connected via wireless to router. Downstairs is connected to printer/scanner all in one. I currently have printer able to accept print jobs from upstairs via system->printing->menu: server->settings->publish shared printers
This is good as I can send print jobs downstairs to print. But I want to scan downstairs, and have the file in a folder that is shared by both computers. Scan downstairs and be able to grab file in upstairs computer without having to put it on usb stick to get on upstairs computer.

Is there a quick default way to do this in ubuntu?

I don't currently have 10.10 installed on either computer but will once released. I've tested 10.10 though. 10.04 downstairs 9.10 upstairs currently.

Please don't suggest Ubuntu One as I don't want these files going on the internet. I figure it should be just as easy as sharing printer over router network. But I don't see any quick way to do this.

I've used remote desktop viewer before to run downstairs computer (updates etc), but that has nothing to do with a shared folder that both computers can access.

In future I suppose I'd also want shared folders possible so I can watch video over the network on downstairs computer since media is stored upstairs.

Also one reason for this now is that I did have all in one printer upstairs (and one downstairs), but one upstairs is 8 years old and printer part is not working properly, so will be junking it soon. No need for two.

Now off to google to find solutions. I'm just hoping someone has a good default one for 10.10
Ok first google results says right click folder and tell to share. On my 9.10 install says need to install "the windows network sharing service". Umm ok. Will wait for comment before trying.

With Simple Scan in 10.04 there is no option to default save to. So I have to tell it to scan, then wait for it to finish, then tell it to save, select a folder to save to and filename? Has this been fixed in 10.10? Do I need to install xsane to have automated saving procedures when scanning? I'd prefer to just press scan, then be done with the program, and go upstairs to get the file in saved folder.

---

### Post by ubunterooster on 2010-09-18
You "need to install 'the windows network sharing service' " also known as nautilus-share (a samba program)

---

### Post by cariboo on 2010-09-18
From Linux to Linux, NFS is a far easier way to share directories. For a howto have a look [here]("https://help.ubuntu.com/community/SettingUpNFSHowTo")

---

### Post by andrewabc on 2010-09-18
> **cariboo907 said:**
> From Linux to Linux, NFS is a far easier way to share directories. For a howto have a look [here]("https://help.ubuntu.com/community/SettingUpNFSHowTo")

Thanks for link.
I assume in the link it is describing two ways to accomplish it? NSFv4 and NFS? I presume NFSv4 is newer/better version?

---

### Post by cariboo on 2010-09-18
It's also buggier, use what in the repositories. Remember, newer isn't always better. :) I'm running Karmic on my server, and I won't upgrade till it eol's

---

### Post by davrosuk on 2010-09-18
NFSv4 is in the repo's for Lucid and Maverick. I haven't found it buggy at all - quite the inverse. Very stable and much better performing.

For printing, have a look at CUPS. Dead easy to set up and it'll turn that standalone printer into a network one ;-)

---

### Post by cariboo on 2010-09-18
I was just going by the README.Debian.nfsv4 file where it states:

> NFSv4 support in Debian is rather new, and not fully supported yet.

File sharing for me needs to be dead reliable, I don't want to be playing with experimental versions.

---

### Post by davrosuk on 2010-09-19
Its rock solid. I wouldn't use it if it wasn't. I've had no problems at all and been using it heavily for ages. I'm really surprised at the readme line since NFSv4 is hardly new now. The RFC is a decade old  and you could get it working on Debian at least 5 years ago. To be honest most of Linux is still classed as experimental though - look at how many packages have a version <1 :-)

---

