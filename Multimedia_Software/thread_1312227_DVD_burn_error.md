---
title: "DVD burn error"
date: 2009-11-03
forum: Multimedia Software
---

### Post by rrsst6 on 2009-11-03
I formatted a .avi in Devede.  I tried to burn the .ISO to a blank dvd using brasero.  I get this error (below).  I've tried using k3b also and no luck.  Some please help!

BraseroGrowisofs Launching command
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs stdout: Executing 'builtin_dd if=/home/ryan/Desktop/movie/movie.iso of=/dev/sr0 obs=32k seek=0'
BraseroGrowisofs called brasero_job_set_dangerous
BraseroGrowisofs stderr: /dev/sr0: "Current Write Speed" is 8.2x1352KBps.
BraseroGrowisofs stdout:           0/9566208 ( 0.0%) @0x, remaining ??? RBU  28.5% UBU   0.0%
BraseroGrowisofs stdout:           0/9566208 ( 0.0%) @0x, remaining ??? RBU  28.5% UBU   0.0%
BraseroGrowisofs stdout:           0/9566208 ( 0.0%) @0x, remaining ??? RBU  28.5% UBU   0.0%
BraseroGrowisofs stdout:           0/9566208 ( 0.0%) @0x, remaining ??? RBU  28.5% UBU   0.0%
BraseroGrowisofs stdout:           0/9566208 ( 0.0%) @0x, remaining ??? RBU  28.5% UBU   0.0%
BraseroGrowisofs stdout:           0/9566208 ( 0.0%) @0x, remaining ??? RBU  28.5% UBU   0.0%
BraseroGrowisofs stdout:           0/9566208 ( 0.0%) @0x, remaining ??? RBU  28.5% UBU   0.0%
BraseroGrowisofs stdout:           0/9566208 ( 0.0%) @0x, remaining ??? RBU  28.5% UBU   0.0%
BraseroGrowisofs stdout:           0/9566208 ( 0.0%) @0x, remaining ??? RBU  28.5% UBU   0.0%
BraseroGrowisofs stdout:           0/9566208 ( 0.0%) @0x, remaining ??? RBU  28.5% UBU   0.0%
BraseroGrowisofs stdout:           0/9566208 ( 0.0%) @0x, remaining ??? RBU  28.5% UBU   0.0%
BraseroGrowisofs stdout:           0/9566208 ( 0.0%) @0x, remaining ??? RBU  28.5% UBU   0.0%
BraseroGrowisofs stdout:           0/9566208 ( 0.0%) @0x, remaining ??? RBU  28.5% UBU   0.0%
BraseroGrowisofs stdout:           0/9566208 ( 0.0%) @0x, remaining ??? RBU  28.5% UBU   0.0%
BraseroGrowisofs stdout:           0/9566208 ( 0.0%) @0x, remaining ??? RBU  28.5% UBU   0.0%
BraseroGrowisofs stdout:           0/9566208 ( 0.0%) @0x, remaining ??? RBU  28.5% UBU   0.0%
BraseroGrowisofs stdout:           0/9566208 ( 0.0%) @0x, remaining ??? RBU  28.5% UBU   0.0%
BraseroGrowisofs stdout:           0/9566208 ( 0.0%) @0x, remaining ??? RBU  28.5% UBU   0.0%
BraseroGrowisofs stdout:           0/9566208 ( 0.0%) @0x, remaining ??? RBU  28.5% UBU   0.0%
BraseroGrowisofs stdout:           0/9566208 ( 0.0%) @0x, remaining ??? RBU  28.5% UBU   0.0%
BraseroGrowisofs stderr: :-[ WRITE@LBA=0h failed with SK=0h/ASC=00h/ACQ=02h]: Input/output error
BraseroGrowisofs stderr: :-( write failed: Input/output error
BraseroGrowisofs stderr: HUP
BraseroGrowisofs stdout: HUP
BraseroGrowisofs process finished with status 5
BraseroGrowisofs called brasero_job_error
BraseroGrowisofs finished with an error
BraseroGrowisofs asked to stop because of an error
    error        = 0
    message    = "no message"
BraseroGrowisofs stopping
BraseroGrowisofs got killed
Session error : unknown (brasero_burn_record brasero-burn.c:2769)

---

### Post by rudy.elgato on 2009-11-08
I'm having a similar problem.  

I'm running with a clean, complete install of 9.10, and am unable to burn an iso (created from an avi using devede) to dvd.  I've tried using both Brasero and K3B, and also tried using a DVD-R and DVD+R, but none works.  I'm using a Samsung SH-S203N 20x DVD-Rom Burner SATA Drive with LightScribe.  

I have run 8.04 and 8.10 on this system and had no problems whatsover burning DVD to the same Samsung drive.

Any ideas on what to check?

Thanks...

---

### Post by gdonwallace on 2009-11-08
The first thing I would suggest is to try and do the burn without the formating.  I am running 9.10 and have burned several CD / DVD without any problem.  The only difference is that I do not format the CD / DVD before burning.

---

### Post by rudy.elgato on 2009-11-08
in my situation, I've never formatted a disk prior to burning to it.  all work was handled by k3b and/or brasero.

BTW, I am able to burn an audio CD without any problems.  this uses the same drive as used for DVDs.  so, burning CDs, no problem, burning DVDs, can not do...

Thanks...

---

### Post by rudy.elgato on 2009-11-09
rrsst6...

found a fix, at least for my situation...

I ran item #2 in [http://art.ubuntuforums.org/showpost.php?p=7185976&postcount=34](http://art.ubuntuforums.org/showpost.php?p=7185976&postcount=34), and I've been able burn dvds again.  Apparently there are quite a few reported issues related to "wodim".  Anyhow, like I said, running 'sudo chmod u+s /usr/bin/wodim' seems to correct the problem I was having.  Just hoping it permanent.

A few things I did notice afterwards when running 'k3b':

- the little spinning icon that usually just shows up for a second or so while a gui opens, remains constantly spinning.  it's a little odd, makes you think something is stuck, but even though it's spinning, all button selections are live.  
- there's no indication that the checksum is running.  typically as soon as you select the iso to burn in k3b the md5 checksum is run, and you see the indicator bar increasing in size until it reaches the end and you end up with your checksum total.  for me, the bar does not show up at all.  eventually after a minute or so, the time it typically takes for the checksum to run, the checksum total appears.  could be related to the spinning busy icon.  who knows...
- I didn't try burning anything faster then 4x.  

Anyhow, maybe the 'chmod' will help you as well...

---

### Post by claypole on 2009-11-22
I had a nightmare with the "SK=3h/POWER CALIBRATION AREA ERROR" error on a LITE-ON LH-20A1H, trying to burn a 3Gb DVD ISO.

After much searching and no clear answer I found this link [http://codeguys.rpc1.org/firmwares.html](http://codeguys.rpc1.org/firmwares.html) through another forum related to this problem that enabled me to upgrade the firmware of my drive (using the .exe and WINE).

Now it all works fine and at the full 8X speed :guitar:

Hopefully this will help others with this very frustrating problem.

---

### Post by anoopkmohan4u on 2010-06-19
[SIZE=3]Iam using PBDS DS-8W1P Slim 8x DVD+/-RW
iam getting the same message and not able to write a dvd that i created from DeVeDE.
please help me or the only option i have is to format and install every thing from the beginning...
Please Help me with this issue.
This is the first help iam asking in this ubuntun  forum.

waiting for the reply
[email]Anoopkmohan4u@gmail.com[/email]

[/SIZE]

---

### Post by seanbrannon on 2010-06-25
> **rudy.elgato said:**
> rrsst6...

found a fix, at least for my situation...

I ran item #2 in [http://art.ubuntuforums.org/showpost.php?p=7185976&postcount=34](http://art.ubuntuforums.org/showpost.php?p=7185976&postcount=34), and I've been able burn dvds again.  Apparently there are quite a few reported issues related to "wodim".  Anyhow, like I said, running 'sudo chmod u+s /usr/bin/wodim' seems to correct the problem I was having.  Just hoping it permanent.

A few things I did notice afterwards when running 'k3b':

- the little spinning icon that usually just shows up for a second or so while a gui opens, remains constantly spinning.  it's a little odd, makes you think something is stuck, but even though it's spinning, all button selections are live.  
- there's no indication that the checksum is running.  typically as soon as you select the iso to burn in k3b the md5 checksum is run, and you see the indicator bar increasing in size until it reaches the end and you end up with your checksum total.  for me, the bar does not show up at all.  eventually after a minute or so, the time it typically takes for the checksum to run, the checksum total appears.  could be related to the spinning busy icon.  who knows...
- I didn't try burning anything faster then 4x.  

Anyhow, maybe the 'chmod' will help you as well...

I had the same problem and this fixed it. Thanks. I was able to write at 6x using CD/DVD creator.

---

