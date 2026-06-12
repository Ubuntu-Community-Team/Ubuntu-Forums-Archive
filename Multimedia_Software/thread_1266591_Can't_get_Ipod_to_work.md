---
title: "Can't get Ipod to work"
date: 2009-09-14
forum: Multimedia Software
---

### Post by sidious1741 on 2009-09-14
I have tried EVERYTHING (Banshee, gtkpod, rhythmbox, amarok).  I got something to happen with gtkpod but I don't know how and I can't do it again.  With gtkpod, I can't even select the right model number (A1199).  While still looking for a solution, I will try to install itunes with wine.

---

### Post by sidious1741 on 2009-09-14
I would just do it in VirtualBox Windows but I can't find the data on the disk or even use a flash drive to transfer files.  I would also hope that there is a different solution; VirtualBox runs SOO slow.

---

### Post by sidious1741 on 2009-09-14
I failed at installing itunes because I cannot find 8.2.  I would be happy to download 9.0 but winehq calls it "garbage" compared to 8.2, "silver"

---

### Post by lduperval on 2009-09-14
I use gtkpod with an older iPod. 

Does your machine mount the iPod, at least?

L

---

### Post by sidious1741 on 2009-09-15
> **lduperval said:**
> I use gtkpod with an older iPod. 

Does your machine mount the iPod, at least?

L

Yes, like I said, I somehow got it to work one time.  All the programs recognize the device and can see the music files on it.  I just can't get anything else on the device.

---

### Post by traderjb on 2009-09-20
Newbie..well actually haven't used Ubuntu in years. Anyways, I just purchased an iPod Touch, and as well cannot get it to work with the OS.  Perhaps I'm missing something here, anyone care to point me in the right direction?  Thanks!

---

### Post by sidious1741 on 2009-09-25
> **traderjb said:**
> Newbie..well actually haven't used Ubuntu in years. Anyways, I just purchased an iPod Touch, and as well cannot get it to work with the OS.  Perhaps I'm missing something here, anyone care to point me in the right direction?  Thanks!

That depends on what you mean by "can't get it to work."  You must be more specific.  With a post like that anyone who might have an answer will first ask you "What do you mean?  What doesn't work?"  Your iPod may not be recognized by the system (if you have jail-broken it), your comp may have tried to download something onto the iPod but couldn't and gave a weird error message, or maybe even your cord doesn't work.  Anyway, if you want any help, you need to give more details.

---

### Post by Campbell9 on 2009-10-25
Hi, I see that there are two issues, 1. Runing iTunes and 2. Downloading music from ipod onto the computer. To answer question 1. running iTunes. I do not bother. Amarok or Banshee is just as good. I am trying both so I have no firm opinions yet. Admittedly I also have a Mac Laptop and wil buy music from iTunes and then transfer it onto ipod and then I can transfer music from iPod onto Ubuntu. Which leads me to answer question 2. How to transfer music from iPod onto Ubuntu. 
- Connect Ipod to usb port and use rhythmbox to open ipod ( I am using Jaunty). 
- Click ipod icon in Rythmbox on lefthand side
- Select all songs
- Click and drag music files into the library's music folder (still within Rhythmbox).
- You can now import your songs from the music folder on your computer into any music player of your choice.

---

### Post by THD042 on 2009-10-26
The PITA is that with newer Nanos, probably also with others, this ain't gonna work
as advertised. 
Virgin iPods, connected to a Mac will have HFS file systems on them, which you will be
able to read, but not to write under Linux. So it is a good idea to have a frien with a Windows machine to reinstall everything. I missed the occasion of checking if my new Nano had already Fat32 from the start or not, so this part is speculation. Plug it to you Ubuntu box, try to copy something to it and hope that this will keep a Mac iTunes ruining your day. Take a video, if all else fails :-)

Then, Apple keeps changing specs from generation to generation. The older iPods have a database format that libgtkpod groks, based on some strange CPU with Motorola byte order, and IIRC, 3  Bytes/word. Completely insane. 
My wife's 4GB shuffle has similar databases, but with 32bit words and Intel byte-order. So far, not supported by libgtkpod. My new Nano shuffle has SQL3Lite databases on it, but I have not yet figured out how to really write and update items on it. 

So if the iPod is old enough, the methods of Campbell9 work, but with the brand new ones: fail.

---

### Post by penquin on 2009-10-26
if you started using it on a mac have you tried to make it so you can use it as an external hard drive?  Even though I started using mine in windows I had that option set before I switched.  To copy music from ipod to music library is simple(or so it appears to me)  go inside ipod from nautalis find ipod control folder open it then find music folder open it all those new folders you see is all of your music select all and drag to music folder.  That should do it.

---

### Post by JugglinPhil on 2009-10-26
Anybody ever tried the music player Songbird? After you've intalled the add-on 'Ipod Device Support' it should work without a problem. Try it and tell me what you tink. :)

---

### Post by motorhead_1 on 2009-10-27
edit

---

