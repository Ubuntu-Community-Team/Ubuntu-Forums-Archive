---
title: "Wireless Asus 1000he problems - I'm ready to throw it out the window!"
date: 2009-03-31
forum: Networking &amp; Wireless
---

### Post by crispeto on 2009-03-31
I just got my Asus 1000he computer and installed Ubuntu Jaunty beta. Everything is working great except if I restart or shut down the computer, it is a complete guessing game whether or not it's going to connect to my wifi network or not. I have an apple laptop, my wife's desktop, and my son's asus 900, all using Jaunty and they have no problems at all. Very frustrating because it's just the 1000he. It actually worked better until I did the Ubuntu updates and after that is when the problems started. No rhyme or reason at all. I use comcast with a Linksys WRT54GS wireless router. Any suggestions?

---

### Post by rekabbelac on 2009-03-31
I'm having the same problem with the 1000HE, except it won't work at all for me. When I initially loaded 9.04 it worked fine, but after updates it stopped working. I erased and reloaded, but am still having the same problem.

The wireless screen just sits on the connecting screen and then pops up as if the wrong password is entered. I've tried tweaking around with the wireless security on the router, but it doesn't seem to make a difference.

I think at this point I'm going to try to load the recovery DVD that came with it and verify wireless is working in windows.

---

### Post by crispeto on 2009-03-31
I woke up this morning and had a reply from a different thread and someone told me to install "linux-backports-modules-jaunty". I did that this morning and so far it's been connecting every time. Hope this helps.

---

### Post by sanjeevpunj on 2009-03-31
Dont throw it out,just give it to someone!

---

### Post by crispeto on 2009-03-31
I wondered when someone was going to give that suggestion:)

---

### Post by ajaysutton on 2009-05-19
I'm in the same boat.  I think I'll try "linux-backports-modules-jaunty".  I'm guessing it's just sudo apt-get install... is that right?

---

### Post by ajaysutton on 2009-05-19
Wow, that actually seemed to work.  That's amazing to me for all the number of times I've re-installed 9.04 and put up different wireless networks devices.

Signal strength seems much worse than it had been, but I am able to connect at least.

I wonder if someone a little more experienced than I could tell me what Linux backports modules are?  I'd be grateful for a bit of understanding.

---

### Post by 4solar on 2009-08-08
I'm struggling with the 1000HE as well.  

Wifi performance under 9.04 or 9.04 netbook remix is terrible (low signal, frequent disconnects undetected by networkmanager).  The module backports, or upgrade to karmic alpha, reliably cause wifi to completely fail.  wlan0 may be up but iwlist wlan0 scan reports nothing found; neither my AP nor any of the half-dozen neighbors APs which always show up.

I've gone back to reinstall 9.04 and 9.04 netbook-remix a couple of times; installing the "backports" kills wifi reliably (and requires me, with my limited skills, to reformat the root partition and reinstall from the CD).

Arrgghhh...

---

### Post by inzaneg on 2009-10-31
I had big wireless problems with 9.04, and tried everything. Then I tried Fedora 11 and wireless worked perfect. So I tried to install kernel 2.6.29.5 (same as Fedora) and had no more problems. :D

I'm now on 9.10 and installed latest kernel (2.6.32-rc5) to get good wireless, but not as good as 9.04 and kernel 29.5.

---

### Post by spaceballl on 2010-04-01
Are there any updates on this? I'm having major wireless issues on ubuntu w/ my 1000he! The same as you all describe! I'm trying 10.04 now to see if I have better luck....

---

### Post by pdc on 2010-04-01
here is a link for diagnostic script that is used predominantly on OpenSuse; the writer contributes to the forum there; it is safe;

it analyses your wireless system; makes recommendations; and has links to how-to descriptions;

if you cannot fix it yourself, post the results of the script back here and some wireless experts may be able to help you

[http://www.linux-tips-and-tricks.de/index.php/collectNWData.sh/Benutzeranleitung/Usersguide-von/of-collectNWData.html#English](http://www.linux-tips-and-tricks.de/index.php/collectNWData.sh/Benutzeranleitung/Usersguide-von/of-collectNWData.html#English)

---

### Post by spaceballl on 2010-04-02
Thanks for the link to the opensuse script. I will surely try it out if I have issues.

So to let everyone know where i'm at right now... I installed 10.04 beta1, and I ran a huge batch of updates while surfing the web. In this time, I did encounter a time where the wifi stopped working until i disconnected / reconnected. But after performing all of the updates, so far I've had no issue. I'm hoping it stays that way... The theme is much easier on the eyes now. I also like how there is no list of folders on the right hand side. More room for apps.

---

