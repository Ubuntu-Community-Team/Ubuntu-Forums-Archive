---
title: "vesa VGA - removing generic driver"
date: 2011-02-09
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by ganeshv on 2011-02-09
Hi All
I am relatively fresher in ubuntu ( 8 months), generally use my desktop for making small movies and listen to music.
Unfortunately (unknowlingly) upgraded from 10.10 to alpha 11.04
**[COLOR=navy]currently at kernel - 2.6.38-1[/COLOR]**
During one of the recent upgrades, something happened to my nvidia drivers.
I am not able to go to the command prompt even if I start in **[COLOR=darkred]recovery mode[/COLOR]**.
screen appears to be freezing, just have to do restart
here is the error description:
 
11.862605 [drm] nonveau 0000:00:10.0: misaligned reg 0x001020FB
11.863299 [drm] Pointer to flat panel table invalid
12.660452 fb:confliting fb hw usage nonveaufb vs **[COLOR=darkred]vesa VGA remove[/COLOR]** generic driver
 
Kindly help, I have lots of pictures and videos that I need to recover
please let me know if you guys need more details
Thanks a lot!
Ganesh

---

### Post by [Snc] on 2011-02-09
> **ganeshv said:**
> Hi All
I am relatively fresher in ubuntu ( 8 months), generally use my desktop for making small movies and listen to music.
Unfortunately (unknowlingly) upgraded from 10.10 to alpha 11.04
**[COLOR=navy]currently at kernel - 2.6.38-1[/COLOR]**
During one of the recent upgrades, something happened to my nvidia drivers.
I am not able to go to the command prompt even if I start in **[COLOR=darkred]recovery mode[/COLOR]**.
screen appears to be freezing, just have to do restart
here is the error description:
 
11.862605 [drm] nonveau 0000:00:10.0: misaligned reg 0x001020FB
11.863299 [drm] Pointer to flat panel table invalid
12.660452 fb:confliting fb hw usage nonveaufb vs **[COLOR=darkred]vesa VGA remove[/COLOR]** generic driver
 
Kindly help, I have lots of pictures and videos that I need to recover
please let me know if you guys need more details
Thanks a lot!
Ganesh

You haven't lost anything yet, so be patient ;)

Does the login screen give you some options below the password field, just at the bottom? If so, try 'Ubuntu Classic Desktop', this is the "Fallback" to the old GNOME desktop.

The proprietary drivers for Natty are not ready yet, but the default open source driver works *okay*. You should just disable the FGLRX driver and it should work.

You can go into recovery mode if you press 'e' during boot, from there you can also pick older kernels to boot to.

---

### Post by overdrank on 2011-02-09
Moved to Natty Narwhal Testing and Discussion

---

### Post by Harry33 on 2011-02-09
> **'[Snc] said:**
> 
...
The proprietary drivers for Natty are not ready yet, but the default open source driver works *okay*. You should just disable the FGLRX driver and it should work.
...


Fglrx has nothing to do with this, it is an ATI proprietary driver.
And this is obviously a Nvidia setup.

If the original poster is not an experienced one, my advice is to reinstall Maverick (10.10) after all the important content has been backed up.
Natty (11.04) is a development version, which will introduce a lot of breakages before the release.

---

### Post by ganeshv on 2011-02-09
> **'[Snc] said:**
> You haven't lost anything yet, so be patient ;) 
First of all, thanks a ton for looking into this problem and for the good news!

> **'[Snc] said:**
> 
Does the login screen give you some options below the password field, just at the bottom? If so, try 'Ubuntu Classic Desktop', this is the "Fallback" to the old GNOME desktop.

Unfortunately I am not even reaching the login screen, so I cant really choose any of the options given there. 

> **'[Snc] said:**
> 
The proprietary drivers for Natty are not ready yet, but the default open source driver works *okay*. You should just disable the FGLRX driver and it should work.

Any idea how should I be doing this? In the state that my desktop currently is in, is this doable?
> **'[Snc] said:**
> 
You can go into recovery mode if you press 'e' during boot, from there you can also pick older kernels to boot to.
I tried 6 more previous versions, but I get the above mentioned error

Lastly, as mentioned by Harry33, I am ready to go back to 10.10, but is there anyway to recover my old data? I am more worried on the pictures and videos.

---

### Post by Harry33 on 2011-02-09
> **ganeshv said:**
> 
...
Lastly, as mentioned by Harry33, I am ready to go back to 10.10, but is there anyway to recover my old data? I am more worried on the pictures and videos.

Boot with live-CD (choose try Ubuntu, without installing it),
use Maverick CD and the same architecture (32-bit or 64 -bit) you have.
Then mount the partition where your files are and you get access to them.

---

### Post by zika on 2011-02-09
Once You do backup of things You want to have on a secure place (*), installing Maverick could preserve Your whole /home folder, even though it is not on a separate partition, if You choose not to format partition You are installing it on, just leave as it is. Yes, there might be some glitches with settings in hidden sub-folders, but they are minor issue. You'll have the whole data-structure You're used to, and You'll have (from previous effort (*) a secure backup of those...
I've used this option without formatting partition several times and it worked, always. like a charm. Great asset...

---

### Post by Harry33 on 2011-02-09
> **zika said:**
> Once You do backup of things You want to have on a secure place (*), installing Maverick could preserve Your whole /home folder, even though it is not on a separate partition, if You choose not to format partition You are installing it on, just leave as it is. Yes, there might be some glitches with settings in hidden sub-folders, but they are minor issue. You'll have the whole data-structure You're used to, and You'll have (from previous effort (*) a secure backup of those...
I've used this option without formatting partition several times and it worked, always. like a charm. Great asset...

I would encourage anyone not having a separate /home partition to create one at the very next installation.
Harddisk space is not that expensive, not even SDD.

---

### Post by ganeshv on 2011-02-09
> **Harry33 said:**
> Boot with live-CD (choose try Ubuntu, without installing it),
use Maverick CD and the same architecture (32-bit or 64 -bit) you have.
Then mount the partition where your files are and you get access to them.

Thanks a lot Harry, I could recover 40% of my data, thanks!
But some folders are not letting me copy because of permissions issues, I cannot copy them because of the permissions.
Its strange, how come some folders have permissions and others do not.
is there any way

---

### Post by Harry33 on 2011-02-09
> **ganeshv said:**
> Thanks a lot Harry, I could recover 40% of my data, thanks!
But some folders are not letting me copy because of permissions issues, I cannot copy them because of the permissions.
Its strange, how come some folders have permissions and others do not.
is there any way

Copying does not demand any permissions.
You mean you do not have access to the partition?
Your password should work.

---

### Post by ganeshv on 2011-02-09
> **zika said:**
> Once You do backup of things You want to have on a secure place (*), installing Maverick could preserve Your whole /home folder, even though it is not on a separate partition, if You choose not to format partition You are installing it on, just leave as it is. Yes, there might be some glitches with settings in hidden sub-folders, but they are minor issue. You'll have the whole data-structure You're used to, and You'll have (from previous effort (*) a secure backup of those...
I've used this option without formatting partition several times and it worked, always. like a charm. Great asset...
Thanks Zika for your tip, my system is dual boot, Ubuntu and then vista.
If I use live CD, and rewrite existing Ubuntu with 10.10, will there be impact on GRUB, and can I boot is the same way as I am doing now.
Also harry33, I do not have separate partition for /home, This time I will try for sure after successful data recovery

---

### Post by ganeshv on 2011-02-09
> **Harry33 said:**
> Copying does not demand any permissions.
You mean you do not have access to the partition?
Your password should work.
I have access to partition. I am able to access /home/XXXX/Documents folder.
I have multiple folders for Pictures and videos under Documents and I am able to copy some of the folders under Pictures, others it mentions access denied. (same case under folders for videos too)

Reg password, I am not sure, it did not ask me for any password at any time.
I am using the live Cd boot option and it did not ask for any password at any time. :confused:

---

### Post by Harry33 on 2011-02-09
> **ganeshv said:**
> I have access to partition. I am able to access /home/XXXX/Documents folder.
I have multiple folders for Pictures and videos under Documents and I am able to copy some of the folders under Pictures, others it mentions access denied. (same case under folders for videos too)

Reg password, I am not sure, it did not ask me for any password at any time.
I am using the live Cd boot option and it did not ask for any password at any time. :confused:

You obviously have some errors concerning permission under /home folder.
All subfolders and files in there should have same permissions.
What I meant was, that copying from does not demand permissions, but pasting to may demand.
So, if you have even one folder where you can paste to, use that for your files. Just remember not to format that partition.
It would be better if you could move those files away from partitions, that will be used for installation.

---

### Post by zika on 2011-02-10
> **ganeshv said:**
> Thanks Zika for your tip, my system is dual boot, Ubuntu and then vista.
If I use live CD, and rewrite existing Ubuntu with 10.10, will there be impact on GRUB, and can I boot is the same way as I am doing now.
Also harry33, I do not have separate partition for /home, This time I will try for sure after successful data recoveryI think (I'm pretty sure...) You're OK since You are updating Ubuntu, not messing with Win...

---

