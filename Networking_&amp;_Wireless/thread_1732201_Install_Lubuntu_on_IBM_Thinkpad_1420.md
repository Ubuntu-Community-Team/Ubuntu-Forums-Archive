---
title: "Install Lubuntu on IBM Thinkpad 1420"
date: 2011-04-17
forum: Networking &amp; Wireless
---

### Post by jukingeo on 2011-04-17
Hello all,

I had dug up my wife's old laptop computer from around 1999 (ish) and it is currently running Windows 98 SE.   What I would like to do is set up this machine just to go on to the internet and do general web browsing and emails.  I don't intend to run very heavy games on it.  However, I would like the internet connection to be wireless via a Wi-Fi connection.  This would allow me to use the computer anywhere in the house.   My operating system of choice is Lubuntu 10.10.

I will go over the specs of the Thinkpad (as far as I know).

It has a CD ROM and a floppy built in.  There is an 8 gig (yes that is right 8 gig) hard drive and only 256meg of ram.  It has a com port and one usb port (yes, that is right, only ONE usb port).  It does have a PS2 connector for an external mouse, and a VGA jack for an external monitor.  It has 3D (4 channel) sound. 

It has a slot for a pcmcia card too. The pcmcia card currently in the machine is a Xircom 10/100 network card (Model XE2000).

Tonight I made an attempt to load up the Live CD version of Lubuntu.  The computer DID take the OS, but it took about 15 minutes to load!! :o.

When trying to access the internet via the browser, I naturally got the typical "page not found" error message.  Right away I assumed this probably could be an issue with Lubuntu trying to communicate with the pcmcia card.  I verified this by noticing that none of the lights on the PC card were flashing.

Now this does get me to thinking that the pcmcia card system is outdated and I am wondering if Lubuntu would even support it.  Anyway, that is one of the reasons I am posting here.  I would like to get the pcmcia card working if possible.

I am hoping that I could use a pcmcia WiFi card on this machine because I do not want to occupy the sole USB port.  With only 8 gigs to play with on the Hard Drive, I certainly will need another avenue of memory storage on this machine.  I did a bit of research and I am not sure if I can put a bigger hard drive into this machine.

So, bottom line, can this computer be used for just the purpose of wireless internet?  Or is it just so old that I should retire it completely.

Thank You,

Geo

---

### Post by jukingeo on 2011-04-17
Hello All,

I have a very old IBM Thinkpad 1420 that I would like to use to just browse the internet and read emails from anywhere around the house.  In a nutshell, I would like to recycle this old machine to use as a netbook.

The machine is from 1999 and it is severely outdated with only 256meg of ram and an 8 gig hard drive (yes, you read correctly...it is only 8 gig).  As far as I can see, I don't think the hard drive can be updated.  This is one of the reasons why I just want to delegate this machine to internet use only.

The saving grace this machine has is that it is full featured.  It has 3D sound, a built in Floppy AND CD-Rom.  It also does have one (yeah only one) USB port.  Finally there is the pcmcia card.  As of now I have a Xircom XE2000 Network card in there and it works with the current Windows 98 operating system.

Last night I tried to run the Live CD of Lubuntu and it seems as if it couldn't access the pcmcia card as none of the card's lights came on.

At any rate, I am intending to replace the Xircom card with a Wi-Fi card, if that is possible.

Would anyone recommend a Wi-Fi card that is known to work on these older laptops with Lubuntu?

Thank You,

Geo

---

### Post by mörgæs on 2011-04-18
I have Lubuntu running on a similar machine (a Compaq, but similar age). It works surprisingly well.

8 GB of hard drive space is plenty. There is no need for buying more.

First step is to install Lubuntu having wired internet access. When this works, we can focus on the wirefree.

---

### Post by wolfen69 on 2011-04-18
> **jukingeo said:**
> 
So, bottom line, can this computer be used for just the purpose of wireless internet?  Or is it just so old that I should retire it completely.


Yes it could be, but if you're just surfing with it, I would use something lighter like puppy linux. But puppy is a completely different animal.

---

### Post by cariboo on 2011-04-18
Please don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by jukingeo on 2011-04-18
> **mörgæs said:**
> I have Lubuntu running on a similar machine (a Compaq, but similar age). It works surprisingly well.

8 GB of hard drive space is plenty. There is no need for buying more.

First step is to install Lubuntu having wired internet access. When this works, we can focus on the wirefree.

Ok, fair enough...then can someone help me get the existing Xircom XE2000 PC card to work?  I wasn't sure if this card is Linux supported.  Bottom line is that if it isn't, I certainly will NOT buy another wired card, but would go the route of a wireless card.

> **wolfen69 said:**
> Yes it could be, but if you're just surfing with it, I would use something lighter like puppy linux. But puppy is a completely different animal.

I have used Puppy before in the past (about two to 3 years ago) and it was kind of limited in regards to available applications.  However, I would gather that has improved over time.  I would think that if it can do wireless on a PCMCIA card, then it should be good enough.  As it is I am mostly going to use it for surfing, emailing, and the occasional download (which could be stored on a memory stick).

> **cariboo907 said:**
> Please don't create multiple threads on the same subject, I have merged your two threads.

Technically the subject is different:  One is installing Lubuntu, the other is setting up wireless.  But yes, it is for the same machine, so the content is *similar* :).

So I guess the new question would be if I should use Puppy Linux and can I get that to work via wireless on a PCMCIA card?

Thanx,

Geo

---

### Post by jukingeo on 2011-04-21
Hello All,

Does anyone have some suggestions for what wireless (for WiFi) PCMCIA card I should use with this laptop computer?

Thank You,

Geo

---

### Post by josephmills on 2011-04-21
have you ever thought about adopting a puppy? [http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm](http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm)

---

### Post by mörgæs on 2011-04-22
If you don't have a real RJ-45 port, what about a USB to RJ-45 adaptor?

---

### Post by cavalier911 on 2011-04-22
To get your xircom ethernet adapter functioning:
```
sudo modprobe xirc2ps_cs
```
Followed by:
```
sudo service network-manager stop
```
```
sudo service network-manager start
```
or add **xirc2ps_cs** to /etc/modules to auto-load on boot. 
Reboot.
Until you install a wireless card and run ```
lspci -nn 
```there's no way to know what chipset it has. Most of the 32 bit cards do have native drivers available.

---

### Post by jukingeo on 2011-04-22
> **josephmills said:**
> have you ever thought about adopting a puppy? [http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm](http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm)

Yes, I have.  I am no stranger to Puppy as I was tinkering with it for a possible JOrgan (Virtual Pipe Organ) project.  

I have recently looked into the new version and even left a similar post in the Puppy forums to see what response I would get as to what PCMCIA card I should get.

> **mörgæs said:**
> If you don't have a real RJ-45 port, what about a USB to RJ-45 adaptor?

The computer doesn't have built in network capabilities...only a 'cough' modem.  So the Xircom card was added later to give the computer connection abilities to high speed internet.

I already have an Entegra USB to RJ-45 adapter, but I choose not to use it as I want to go wireless on this machine AND since I mentioned that the machine only has ONE usb port, I would rather not use that for the wireless connection.  Very simply, I would want to use the USB port for a memory stick should I want to download something.  Granted I could use a small USB hub for more ports...but that kind of takes away from the wireless portability of the setup if you have this "octopus" hanging from the back of my laptop.

> **cavalier911 said:**
> To get your xircom ethernet adapter functioning:
```
sudo modprobe xirc2ps_cs
```
Followed by:
```
sudo service network-manager stop
```
```
sudo service network-manager start
```
or add **xirc2ps_cs** to /etc/modules to auto-load on boot. 
Reboot.
Until you install a wireless card and run ```
lspci -nn 
```there's no way to know what chipset it has. Most of the 32 bit cards do have native drivers available.

So that kind of bounces back to my original question.  Should I even bother with trying the Xircom adapter?  Wouldn't I be better off buying a wireless card that I know would work?

Thanx,

Geo

---

### Post by mörgæs on 2011-04-23
> **jukingeo said:**
> 
I already have an Entegra USB to RJ-45 adapter, but I choose not to use it as I want to go wireless on this machine 

I know that this is the final aim, but does everything work 100% on the wired connection, and have you applied all updates to 10.10? I would guess around 300 packages needs updating after a fresh install.

---

### Post by jukingeo on 2011-04-24
> **mörgæs said:**
> I know that this is the final aim, but does everything work 100% on the wired connection, and have you applied all updates to 10.10? I would guess around 300 packages needs updating after a fresh install.

No, the wired connection doesn't work either.  I am not working off a full install of Lubuntu 10.10, as I am 'testing' it via the Live CD.   

As of now the computer does work with the existing Windows 98 system.  It is just that the programs for Win98 on the machine are terribly outdated.  As such I was going to go a lighter weight operating system as I am using Ubuntu Studio on my main computer.  I figured Lubuntu would be fine for the Thinkpad 1420.  However, I am beginning to think that Lubuntu might not be the right choice after all.   As it stands it takes and AWFUL long time to boot up from the Live CD.

As another poster suggested, I have been trying my luck out with Puppy Linux.  The good news is that Puppy boots up (Live CD) in less than HALF the time.  The bad news, it still doesn't recognize the PCMCIA card.  However, I have ran a test on the computer via a program called "PupScan", and it DOES see the PCMCIA slot as it comes up with a detected Yenta_Socket cardbus.  So that is a plus.  It means that Puppy Linux is seeing the the PCMCIA system, but it doesn't know what to do with the Xircom network card.

Thus the way things are headed, I think I am done with trying to get Lubuntu to run on this machine and I am leaning more to sticking with Puppy.

But I am open to any suggestions or ideas otherwise.

Thank You,

Geo

---

