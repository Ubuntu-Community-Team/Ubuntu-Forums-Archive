---
title: "Need to encrypt the DVDS for copying!!!"
date: 2008-04-25
forum: Multimedia Software
---

### Post by tyreads on 2008-04-25
Hello everybody, I have a collection of DVDS and would like to continue with that. I sometimes do make copies of the original ones if I am not able to get them but the problem is that some are encrypted and couldn’t be copied. I am looking for a tool that can copy the encrypted ones and be efficient in speed and quality too.


Hope to get your suggestions!!!!

---

### Post by fhantazm on 2008-04-25
This is only used for DVDs you own. Anything else is pirating. There are many methods, here is one:



Tested on Ubuntu 7.10 (Gutsy Gibbon) (It works for me in Hardy as well)

But before we start, make sure you have the multiverse repository enabled.

To enable it:

1.. Open synaptic package manager. (System-->Administration-->Synaptic Package Manager)

2. Now, in synaptic go to the package sources (Settings-->Repositories), and enable the multiverse one. ("Software restricted by copyright or legal issues (multiverse)").

3. Now click "Close", and then click the "Reload" button in synaptic. There we go. All done. Now to move on to the tutorial.

Backup DVDs in Ubuntu

Step 1: Install a program called "k9copy", by running this command in the terminal.
Code:
sudo apt-get install k9copy


Step 2: Wait for it to get done installing, open it up (Applications-->Sound & Video-->k9copy).

Step 3: Now, put your DVD in the drive. And click "File-->Open", to open the DVD in k9copy.

Step 4: Check the check box of the DVD. And now click either, "DVD" at the top, or "MPG4" at the top. "DVD", will create an ISO image of the dvd, so you can burn it to another DVD. "MPG4", will create a video file, that will let you watch the movie on your computer. (Such as Movie Player, or VLC). If you chose "MPG4" skip to step 7.

Step 5: If you chose DVD, simply choose where you want the ISO, then wait for it to get done ripping. It will soon say it's burning. It's not really burning, it's creating an ISO image.

Step 6: Now, the ISO file will be where you told it to save it to. What you do it Right Click on it, and then click "Write to Disc...", insert your blank disc, and let iy write. There ya go. A great copy of your DVD.

Step 7: If you chose MPG4, just choose the place where you want to save the video. And then wait for it to get done.

Step 8: Enjoy watching your new DVD or video file.

---

### Post by blastus on 2008-04-26
> **tyreads said:**
> Hello everybody, I have a collection of DVDS and would like to continue with that. I sometimes do make copies of the original ones if I am not able to get them but the problem is that some are encrypted and couldn’t be copied. I am looking for a tool that can copy the encrypted ones and be efficient in speed and quality too.


Hope to get your suggestions!!!!

You can use DVDFabHDDecrypter but it requires Windows. Then you can use mkisofs with the -dvd-video option in Linux to create an .iso image file.

---

### Post by Fernando23 on 2008-04-26
I too had the same problem of copying the DVDS which were encrypted (I do not collect dvds) but I have to copy them for my business .I had used many software’s till date but recently found a [ DVD Cloner ]( http://dvd-cloner.software-com.com/)  that does the decryption and also maintains the speed and quality like the original one.


Hope that you would find it useful.

---

### Post by ksbaker on 2008-04-27
Hi-I am going to try k9copy as you suggested-I am having problems with dvdrip though.  It seems to rip fine but when I burn the dvd with brasero or gnomebaker the fourth vob is in spanish when i play it on my television's dvd player.  the rest is in english.  i was wondering if anyone else has had this particular problem with their dvds and how to fix it? thanks

---

### Post by bricedebrignaisplage on 2008-08-02
Can this tool be used to make an unencrypted copy of an encrypted DVD. I have a couple of encrypted DVDs that my home theatre system cannot read, and it's a pain to watch them on my computer...

Also: I installed libdvdcss2 but Kaffeine still cannot read the encrypted DVDs, not Mplayer. I can only read them with VLC. Kaffeine tells me "This DVD Video is encrypted. To be able to watch it you will need to install libdvdcss by running from a console: sudo /usr/share/doc/kaffeine/install-css.sh" but it doesn't work.

---

### Post by smuggly on 2008-08-03
Youll Need libdvdcss3 libread  w32Codecs  Or w64codecs Whichever Applies Then U Can Do It With K9Copy ......   Smuggly


Check Out This Link.If Theyl Play U Can Rip Em!
[http://ubuntu-tutorials.com/2008/01/29/medibuntu-the-only-3rd-party-repo-i-use/](http://ubuntu-tutorials.com/2008/01/29/medibuntu-the-only-3rd-party-repo-i-use/)

---

