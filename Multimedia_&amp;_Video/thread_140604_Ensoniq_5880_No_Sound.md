---
title: "Ensoniq 5880 No Sound"
date: 2006-03-06
forum: Multimedia &amp; Video
---

### Post by screamingindigital on 2006-03-06
I have a fresh install of 5.10 and everything is working except the sound.  In the device manager it lists my card as a Creative Sound Blaster AudioPCI 128 Ensoniq 5880.  The box that it came in says it is a Soundblaster 16 PCI.  Here is what I have done so far:

The output of "cat /proc/asound/cards" for my PC is:
--- no soundcards ---

output for lsmod | grep ens
snd_ens1371            22240  0
gameport               14472  1 snd_ens1371
snd_rawmidi            22816  1 snd_ens1371
snd_ac97_codec         72188  1 snd_ens1371
snd_pcm                78344  3 snd_ens1371,snd_ac97_codec,snd_pcm_oss
snd                    48644  8 snd_ens1371,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer

sudo modprobe snd-ens1371 returned nothing

lspci reports:
0000:00:0a.0 Multimedia audio controller: Ensoniq 5880 AudioPCI (rev 02)

sudo esd says :
ALSA lib pcm_dmix.c:802:(snd_pcm_dmix_open) unable to open slave

lsmod reports:
snd_ens1371            22240  0

I have done a search on this forum and tried just about everything that I could find.  I have used this card w/ other distro (suse, mandrake, etc) and they were able to find it.  Any help would be appreciated.  \\:D/

---

### Post by screamingindigital on 2006-03-07
anyone???  :(

---

### Post by Slim Odds on 2006-05-11
I have the same card, which works fine in Breezy (5.10) but does **not** work in Dapper (6.06)

Very frustrating! ](*,)

Other than that, Dapper is **fantastic!!!**  :D

---

### Post by x2l2 on 2006-06-12
same problem here :(

same results that screamingdigitla has...

esd: 
ALSA lib confmisc.c:672: (snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3493: (_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392: (snd_func_concat) error evaluating strings
ALSA lib conf.c:3493: (_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1072: (snd_func_refer) error evaluating name
ALSA lib conf.c:3493: (_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3962: (snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2102: (snd_pcm_open_noupdate) Unknown PCM default

---

### Post by sjeapes on 2006-07-26
I've got the same problem.

I have already tried the steps in the comprehensive sound solutions post but to no avail.

I had this problem in Breezy too though :(  (it worked in Hoary).

Any suggestions?

---

### Post by Davilinux on 2006-08-24
Hi all!!

Did you tried adding "acpi=ht" to your GRUB/LILO?

I was like you, trying to "hear something" from my box, but nothing at all, searching and testing all the answers I've found... until I made the next modification of GRUB (that I read about a shutdown problem):

(extract from my /boot/grub/menu.lst)

[I]title           Ubuntu, kernel 2.6.15-25-386
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.15-25-386 root=/dev/hdb1 ro quiet splash vga=788 [SIZE="3"]**acpi=ht**[/SIZE]
initrd          /boot/initrd.img-2.6.15-25-386
savedefault
boot
[/I]

... and now I can hear my music, videos, system sounds ...  =D>

---

### Post by sjeapes on 2006-08-24
Woooo hoooo!!!! It Works :biggrin: :biggrin: :biggrin: 

I can hear sound!

Thanks a lot Davilinux  =D>

---

### Post by Zer0Nin3r on 2006-10-06
> **Davilinux said:**
> Hi all!!

Did you tried adding "acpi=ht" to your GRUB/LILO?

I was like you, trying to "hear something" from my box, but nothing at all, searching and testing all the answers I've found... until I made the next modification of GRUB (that I read about a shutdown problem):

(extract from my /boot/grub/menu.lst)

[I]title           Ubuntu, kernel 2.6.15-25-386
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.15-25-386 root=/dev/hdb1 ro quiet splash vga=788 [SIZE="3"]**acpi=ht**[/SIZE]
initrd          /boot/initrd.img-2.6.15-25-386
savedefault
boot
[/I]

... and now I can hear my music, videos, system sounds ...  =D>
The simple command: **acpi=ht** was a huge success!  And took very little time, just a little searching for keyword: **5880** and a little reading.

How did you come to that conclusion? (shutdown problem?)

---

### Post by Zer0Nin3r on 2006-10-06
Now is there a way to keep the settings instead of re-configuring everything (including wifi (hawkings HWP54G)) when a new update is installed?  Do I have to create a script?

---

### Post by eeried on 2006-10-09
Was that on a laptop?

On a desktop this card works fine -- no tweaking required.

cheers,

---

### Post by mjpoetic on 2006-11-07
> **Zer0Nin3r said:**
> Now is there a way to keep the settings instead of re-configuring everything (including wifi (hawkings HWP54G)) when a new update is installed?  Do I have to create a script?

Thank God for this post!!  I was setting this up on an old computer for my family.  To answer your question...just add acpi=ht to the kopt section in your /boot/grub/menu.lst file.  Find this section and add it where I bolded the text:

```

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=efb07b7f-e427-4322-9935-019780661c57 ro
# kopt_2_6=root=/dev/hdb5 ro **acpi=ht**
```

Hope this helps!!

---

### Post by eeried on 2006-11-08
> # kopt_2_6=root=/dev/hdb5 ro acpi=ht

What I don't understand is how a commented line can be active? Don't you have to uncomment the line?

What does ht mean?

Thanks!

---

### Post by mjpoetic on 2006-11-08
> **eeried said:**
> What I don't understand is how a commented line can be active? Don't you have to uncomment the line?

What does ht mean?

Thanks!

I too thought so once upon a time, but that's how it should read.  As for "ht", uh....I dunno.  I was just following instructions.  I would also like to know what that line is saying as well.

---

### Post by mjpoetic on 2006-11-10
Ok...I acted too soon.  The acpi=ht line didn't work for my family's old computer.  I am such a noob!!  Anyway, I am still trying to research other options that could possibly work.  If anyone has any other options I can try...I would greatly appreciate it!  Love this forum!!

---

### Post by Zer0Nin3r on 2006-12-14
> **mjpoetic said:**
> Thank God for this post!!  I was setting this up on an old computer for my family.  To answer your question...just add acpi=ht to the kopt section in your /boot/grub/menu.lst file.  Find this section and add it where I bolded the text:

```

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=efb07b7f-e427-4322-9935-019780661c57 ro
# kopt_2_6=root=/dev/hdb5 ro **acpi=ht**
```

Hope this helps!!

the little command works just fine, it's just that when a major kernel update is put out and I upgrade, I have to go back in and add the line.  Also I have to reconfigure the wi-fi card and I was wondering if anyone has a script that would do all of this for you.

---

### Post by Nattie on 2006-12-27
I tried the acpi=ht and my sound works (es1571) but now my computer will not shut down completely.  I just get a blinking cursor and have to hit the power button.  There is something going on here that's not right.  The Ensoniq card should have modules in the kernel for this card.  I've yet to run across a distro that had problems with this card.  Hope somebody figures this out.  Especially when somebody says card worked in Hoary but not Dapper.  Now does that make sense?

---

### Post by godrox on 2007-01-10
This also fixed my problem with an Ensoniq ES1370 card, but, like Nattie, my system is not shutting off all the way either. Any ideas how to correct this?

---

### Post by rennen01 on 2007-03-11
I tried adding the line and it screwed up on boot up.  Had to go in and manually take the  acpi=ht out and my system came up fine.

Still no sound though.  :(

---

### Post by Lhiata on 2007-06-30
> **Davilinux said:**
> Hi all!!

Did you tried adding "acpi=ht" to your GRUB/LILO?

I was like you, trying to "hear something" from my box, but nothing at all, searching and testing all the answers I've found... until I made the next modification of GRUB (that I read about a shutdown problem):

(extract from my /boot/grub/menu.lst)

[I]title           Ubuntu, kernel 2.6.15-25-386
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.15-25-386 root=/dev/hdb1 ro quiet splash vga=788 [SIZE="3"]**acpi=ht**[/SIZE]
initrd          /boot/initrd.img-2.6.15-25-386
savedefault
boot
[/I]

... and now I can hear my music, videos, system sounds ...  =D>


I have a newb question.

How do you *DO* that..... *sobs, having now spent four consequtive hours trying to hear ANYTHING from my computer.....*:cry:

---

### Post by Legendário on 2008-05-02
My ensoniq 5880 does not work on gutsy and hardy? The acpi=ht option does not work for me because it makes my mouse and keyboard to freeze. Does anyone still have this card fully working on gutsy or hardy?

This could help me a lot :confused:

---

