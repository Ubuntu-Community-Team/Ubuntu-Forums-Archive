---
title: "New Mythbuntu system - can't scan SBS in Australia, DVD won't automount"
date: 2009-03-21
forum: Mythbuntu
---

### Post by Zeedok on 2009-03-21
Hi I have just bought a new HTPC with the following components/specs:

Antec Micro Fusion 350 HTPC Case
Intel Core 2 Duo E8400 CPU 3.0 GHz
Gigabyte GA-EG41M-S2H Mainboard
4GB DDR2 PC6400 (2x2GB) Dual Channel RAM
8X Dual Layer DVD+RW + 20X DVD+-RW + CD-RW Combo Drive
1TB 7200RPM SATA HDD
512MB NVIDIA Geforce 8400GS
Gigabit Ethernet
Hauppauge Nova-T-500 MCE Dual DVBT SD/HD tuner
Mythbuntu 8.10

and I am having a few teething problems.

1.  I have successfully scanned the free to air channels on my two tuners, but several TV stations are missing - especially SBS, SBS HD, SBS News, and a few of the government ones etc (D44, The Christian channel etc).  When I scan for channels I choose "Australia" as my location, so I can't explain why the channels are missing (they scan fine on the HD tuners in my LCD TV)
2.  The DVD drive is not automounting when I enter a disc.  I'm not sure what FSTAB options are necessary to get this to work, but when I mount the drive by other means, and change where mythbuntu looks for the DVD (ie from /dev/dvd to /dvd/scd0 - which seems to be the label of my DVD drive) I can get it to load.
3.  I can't seem to share the free to air aerial cable between the TV and the computer - with a standard DVD recorder (or VCR) you put the aerial into the DVD recorder then another cable from the recorder into the tv (I'm sure it just passes the signal through).  The problem is that I have two "input" aerial connections on the computer and no "outputs" to the tv.  Can I just by a double adapter or splitter??
4.  The button to eject the dvd drive (on the front of the case) does not work.  I guess it has not been connected properly - can anyone point me in the right direction to rectify this?

I'm keen to get these kinks ironed out because they are kind of limiting the enjoyment of my new system - thanks in advance for any help.

PS Can anyone suggest a remote control that will work OTB in Mythbuntu - the one that comes with the case is very limited.

Thanks

---

### Post by Zeedok on 2009-03-21
Can someone please explain to me how to use the "Transport Editor"?

I have found [this post]("http://ubuntuforums.org/showthread.php?t=619062&highlight=sbs+mythbuntu") which seems to solve a similar problem to mine.  I have used the posters parameters (I changed the frequency to 571.5 MHz as this seems to be [the correct SBS frequency for Sydney]("http://vk3khb.gak.net.au/atv/chnlchrt.html")) and entered them into the "Full scan (tuned)" box and the "New Transport" dialog on the transport editor, but even after re-scanning the missing channel does not scan.

Can anyone suggest something to try?

Thanks.

---

### Post by AlecJ on 2009-03-21
> **Zeedok said:**
> Hi I have just bought a new HTPC with the following components/specs:

1.  I have successfully scanned the free to air channels on my two tuners, but several TV stations are missing - especially SBS, SBS HD, SBS News, and a few of the government ones etc (D44, The Christian channel etc).  When I scan for channels I choose "Australia" as my location, so I can't explain why the channels are missing (they scan fine on the HD tuners in my LCD TV)
2.  The DVD drive is not automounting when I enter a disc.  I'm not sure what FSTAB options are necessary to get this to work, but when I mount the drive by other means, and change where mythbuntu looks for the DVD (ie from /dev/dvd to /dvd/scd0 - which seems to be the label of my DVD drive) I can get it to load.
3.  I can't seem to share the free to air aerial cable between the TV and the computer - with a standard DVD recorder (or VCR) you put the aerial into the DVD recorder then another cable from the recorder into the tv (I'm sure it just passes the signal through).  The problem is that I have two "input" aerial connections on the computer and no "outputs" to the tv.  Can I just by a double adapter or splitter??
4.  The button to eject the dvd drive (on the front of the case) does not work.  I guess it has not been connected properly - can anyone point me in the right direction to rectify this?

I'm keen to get these kinks ironed out because they are kind of limiting the enjoyment of my new system - thanks in advance for any help.

PS Can anyone suggest a remote control that will work OTB in Mythbuntu - the one that comes with the case is very limited.

Thanks

1. Try scanning manually, just enter the frequency in full ie. 7 digits

2. The fstab line should read:-
/dev/scd0     /media/cdrom0    udf.iso9660 user.noauto,executf8 0       0
3. Yes you can, but it's lossy, far better is to use an amplified splitter for DVB-T only a few pounds. And use shop bought cables. you would not credit the troubles with home made one's.
4 The button's are not normally remote but part of the drive with a mechanical link. I do it via the remote, then it it is released when unmounted.

I use the Microsoft MCE remote which comes with a USB pick-up unit, bought on-line and edited the ~/.mythtv/lircrc file to use all the buttons.
It's by far the best thing I've bought for my Myth box

---

### Post by Zeedok on 2009-03-22
> **AlecJ said:**
> Yes you can, but it's lossy, far better is to use an amplified splitter for DVB-T

The channels I am missing are quite poor signal strength.  Using a standard splitter I have noticed the qulity is very poor (on the TV which can still evidently get a lock on them).  Do you think an amplified splitter might solve both my problems?

I think I have already tried tuning the channel manually (I may have got the process wrong - or maybe the frequency I suppose) and it didn't work.

Thanks for the tip about the remote, I'll look into it.

Thanks for your help.

---

### Post by jbman on 2009-03-22
SBS seems to be of poor strength in may parts. Its very hit and miss with UHF and DTV.

I have given up with SBS, can only get snow on analogue and nothing picks up with my tv or dvb card.

---

### Post by AlecJ on 2009-03-22
> **Zeedok said:**
> The channels I am missing are quite poor signal strength.  Using a standard splitter I have noticed the qulity is very poor (on the TV which can still evidently get a lock on them).  Do you think an amplified splitter might solve both my problems?

I think I have already tried tuning the channel manually (I may have got the process wrong - or maybe the frequency I suppose) and it didn't work.

Thanks for the tip about the remote, I'll look into it.

Thanks for your help.

Yes it works really well.

---

### Post by Zeedok on 2009-03-22
I read somewhere (on a media centre PC forum I think) that there is a lot of "electrical" noise inside a computer case, so that DVB cards are often setup to be relatively insensitive, meaning that weaker signals are not picked up.  This would seem to explain my problems - I think - as even by splitting my aerial signal with a non-amplified splitter, SBS and the other "missing" channels are much poorer on my TV (which normally picks them up without problems).

So I suspect I will need to get an amplified splitter and hopefully that will fix my problems.

---

### Post by Zeedok on 2009-03-23
> **AlecJ said:**
> 
/dev/scd0     /media/cdrom0    udf.iso9660 user.noauto,executf8 0       0


Sorry this FSTAB entry is no better than the one I already had.  I have also included the demesg and lshal outputs when I insert a disk (ie when it is not accessible).  I have also included the same outputs after the same event from my laptop, which works perfectly.

I'm not sure what it all means, but I am hopeful it will give someone some clues to help me fix this irritation.

Thanks

---

### Post by Zeedok on 2009-03-24
I may have spoken too soon.  The DVD drive now seems to be working well - I think adding the utf8 helped.

Thanks

---

### Post by Zeedok on 2009-04-14
Sort-of solved anyway. 

The DVD drive will usually mount OK, but not always. I have switched to GNOME for my desktop manager (mostly because I'm more comfortable with it) and maybe this has helped, I'm not sure.

I had an aerial guy come out to our building and tweak the system, and now I can scan SBS fine.

Interestingly though, SBS doesn't scan everytime (ie when tuning).  The signal is now quite strong, and having scanned the channel once I can get a lock on the channel no problems, but it is a little odd.

Nonetheless, I am happy enough for now.

---

