---
title: "ATTENTION: Those with broken nvidia after update to 2.6.17.1-10.34 13-Dec-2006"
date: 2006-12-13
forum: Multimedia &amp; Video
---

### Post by jdong on 2006-12-13
**The Situation**
It has come to our attention that a small portion of nvidia users are experiencing a failure to boot into X after today's kernel update.

The problem seems to only happen on some specific configurations involving the unofficial 9631 driver installations and does not appear to affect 877x from the official repositories.

Information is still rolling in and this thread will be updated as more information becomes available.

**Symptoms:**
After applying today's updates and rebooting, the graphical environment does not initialize. You may get a blue screen with an error dialog or just an empty black screen.

If you've applied the updates and rebooted and you can get to a graphical login prompt, **you are not affected by this issue.**.

**Affects:**
This seems to mostly affect people using NVidia driver version 9631 on Edgy Eft. Users using both manually installed and unofficial linux-restricted-modules repositories seem to report this problem.

This doesn't seem to affect those using official nvidia 8xxx drivers from the repositories, or those who are using 9640 beta drivers or higher.
***UPDATE***: One user states that it he is experiencing this issue with the official NVIDIA Legacy drivers too.

This issue does not appear to be as widespread as the problem that happened to Dapper a few months back.

**Cause:**
The root cause is currently unknown and under investigation. It seems to stem from several key nvidia driver files apparently being removed during the update process. these files include:
```

/usr/lib/xorg/modules/drivers/nvidia_drv.o
/usr/lib/xorg/modules/libglx.so

```

This issue appears difficult to reproduce consistently. I am still investigating trying to find a root cause for why those files would be removed by the update process.

**Solutions and Workarounds**
Currently, the solution/workaround involves reinstalling the nvidia drivers. If you installed these nvidia drivers by adding a repository to /etc/apt/sources.list and performing a system update, please issue the following command:
```

sudo apt-get install --reinstall linux-restricted-modules-`uname -r` nvidia-glx

```

If you installed nvidia drivers from an executable downloaded from nvidia.com, please follow the instructions for installing that driver again.

In either case, running this command sometimes has good results, too:
```

sudo depmod -ae

```



Again, details are just beginning to unfold about this issue.


**Please keep clutter down when replying**. Avoid saying something that someone else has already said, use CODE tags or attachments for long output, and otherwise use judgement to make information easy to read for others coming across this thread.[/b]

On behalf of everyone here at Ubuntu, I apologize for any inconvenience this may have caused you.

---

### Post by Roque on 2006-12-13
> **jdong said:**
> **The Situation**
The problem seems to only happen on some specific configurations involving the unofficial 9631 driver installations and does not appear to affect 877x from the official repositories.


I am also having this problem, but with the nvidia legacy drivers, installed from the official repos. I am using Dapper.

---

### Post by daller on 2006-12-13
Doublepost again... What is going on?

---

### Post by daller on 2006-12-13
Should I keep my computer turned ON until this is resolved?

There seems to be a LOT of people suffering from an error 17 in grub after the latest upgrade...

I don't know if this has anything to do with this...

---

### Post by Rodneyck on 2006-12-13
I used this repo..

(32-bit)
deb [http://SeerOfSouls.com/](http://SeerOfSouls.com/) edgy contrib

And installed the drivers with jdong's command listed above, rebooted and still could not get into x server.

---

### Post by Camden on 2006-12-13
Just applied with no problems.  Running 9631 driver for beryl/AIGLX from 
deb [http://www.albertomilone.com/drivers/edgy/nonlegacy/32bit](http://www.albertomilone.com/drivers/edgy/nonlegacy/32bit) binary/

Must be lucky?

---

### Post by Roque on 2006-12-13
I did 
```

sudo depmod -ae

```
rebooted, and I now have full hardware acceleration.

---

### Post by jamesrose on 2006-12-13
I'm just stuck, because I can't remember how I installed it.


EDIT: fixed, forgot i removed the repo.

---

### Post by K.Mandla on 2006-12-13
> **Roque said:**
> I am also having this problem, but with the nvidia legacy drivers, installed from the official repos. I am using Dapper.
Are you sure this is the same problem? I also use the nvidia-glx-legacy from the Dapper repositories, and had no problems with the update or reboot.

---

### Post by PriceChild on 2006-12-13
> **jamesrose said:**
> I'm just stuck, because I can't remember how I installed it.Have you got nvidia-glx installed?

If not, then follow [http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)

---

### Post by Rodneyck on 2006-12-13
> **Roque said:**
> I did 
```

sudo depmod -ae

```
rebooted, and I now have full hardware acceleration.

Are you saying that this is a fix?

---

### Post by Azakus on 2006-12-13
It seems to work for some people, so I'd try it.

---

### Post by Roque on 2006-12-13
> **K.Mandla said:**
> Are you sure this is the same problem? I also use the nvidia-glx-legacy from the Dapper repositories, and had no problems with the update or reboot.
I cannot say this is the same problem. But it has the same symptoms: after a security fix upgrade, I rebooted and lost hardware acceleration (and thus no X); a reinstall of the drivers didn't work; only replacing driver "nvidia" with "nv" in xorg let me access the graphical environment.

[quote="Rodebyck"]
Are you saying that this is a fix?
[/quote]
It worked for me at least.

---

### Post by jdong on 2006-12-13
I added the depmod -ae thing to the first post too. Coincidentally it fixed PriceChild's issue while we were in IRC too.

That's a part of the weirdness with this... there's many different forms of breakage with totally different symptoms upon closer inspection. And, when asked to reproduce the error again by forcing a downgrade and re-upgrade, I've yet to find one person who can do it.

---

### Post by samjh on 2006-12-13
> **jdong said:**
> **Solutions and Workarounds**
Currently, the solution/workaround involves reinstalling the nvidia drivers. If you installed these nvidia drivers by adding a repository to /etc/apt/sources.list and performing a system update, please issue the following command:
```

sudo apt-get install --reinstall linux-restricted-modules-$(uname -r) nvidia-glx

```

If you installed nvidia drivers from an executable downloaded from nvidia.com, please follow the instructions for installing that driver again.

In either case, running this command sometimes has good results, too:
```

sudo depmod -ae

```

In the first suggested solution, are we to substitute "uname" with our own username?  What happens to the brackets?

Is this correct?
sudo apt-get install --reinstall linux-restricted-modules-$(myusername -r) nvidia-glx

Because it tells me linux-restricted-modules cannot be found.

---

### Post by Azakus on 2006-12-13
No. Uname is the system variable for the kernel you have. Don't touch it. DO NOT TOUCH IT! If it still says that it can't find the file, then do this:
```
sudo apt-get install --reinstall linux-restricted-modules-`uname -r` nvidia-glx
```
Again. DON'T TOUCH THE CODE! Just copy and paste.

---

### Post by jdong on 2006-12-13
> **samjh said:**
> In the first suggested solution, are we to substitute "uname" with our own username?  What happens to the brackets?

Is this correct?
sudo apt-get install --reinstall linux-restricted-modules-$(myusername -r) nvidia-glx

Because it tells me linux-restricted-modules cannot be found.

No, those commands were meant to be issued out-of-the-box.

It appears like the $() execution technique doesn't work reliably all the time. I'll replace it with backticks again.

---

### Post by samjh on 2006-12-13
> **jdong said:**
> No, those commands were meant to be issued out-of-the-box.

It appears like the $() execution technique doesn't work reliably all the time. I'll replace it with backticks again.

The $() didn't work for me.  I had to use uname -r by itself, copy down the kernel release number, and subsitute in place of $(uname -r).

Thanks for your extremely fast replies. :)

---

### Post by Rodneyck on 2006-12-13
> **Roque said:**
> I did 
```

sudo depmod -ae

```
rebooted, and I now have full hardware acceleration.

Rogue, thanks. It worked for me as well.  What a nightmare..LOL.  I am off to reinstall beryl.

Thanks again to everyone else.

---

### Post by wgscott on 2006-12-13
> **jdong said:**
> It appears like the $() execution technique doesn't work reliably all the time. I'll replace it with backticks again.

It is specific to bourne-like shells.

tcsh needs the back-ticks.

---

### Post by Roque on 2006-12-13
> **Rodneyck said:**
> Rogue, thanks. It worked for me as well.  What a nightmare..LOL.  I am off to reinstall beryl.

Thanks again to everyone else.
Then many thanks to jdong, who posted the fix. :D

---

### Post by Cariboo1938 on 2006-12-13
Hello,
Yes I'm also one of the victims. I have a problem using the NVIDIA installer, which I downloaded from [www.nvidia.com](www.nvidia.com). I run Ubuntu Edgy-amd64 and I downloaded the NVIDIA driver version 1.0-9631. I had no errors using ```
sudo sh NVIDIA-Linux-x86_64-1.0-9631-pkg2.run
``` . 
But after reboot the computer, my X window server was killed. The black screen was kind of a terminal and I had the login prompt on the screen. With 'vi' I checked on /var/log/xorg.0.log and I found the Error message in > Failed to initialize the NVIDIA kernel module. Please ensure that there is a supported NVIDIA GPU in this system and that the NVIDIA device files have been created properly. 
Aborting: UnloadModul "nvidia"
UnloadModul "ramdac"
UnloadModul "cfb"


I remembered a way to reconfigure the xserver with ```
sudo dpkg-reconfigure -phigh xserver-org
```and was so able to install the old "nv" driver again. I didn't try it again because I was so shocked. Has one an idea what went wrong? Is the file /etc/X11/xorg.conf the reason for the misery?
I have no clue...this is far to much Linux for me!:confused:

---

### Post by edu65 on 2006-12-13
Hi,

I have both the 686 and the 386 kernel and I have just updated both. I am using the stock nvidia-glx-1.0.8776 driver. The strange thing is that rebooting into the 686 kernel is fine, whereas the 386 kernel yields the problem described in this thread. I am using Dapper.

---

### Post by aidanr on 2006-12-14
> **Camden said:**
> Just applied with no problems.  Running 9631 driver for beryl/AIGLX from 
deb [http://www.albertomilone.com/drivers/edgy/nonlegacy/32bit](http://www.albertomilone.com/drivers/edgy/nonlegacy/32bit) binary/

Must be lucky?

same here

---

### Post by samurai1200 on 2006-12-14
So I was affected by this anomaly, but a quick reinstall of the nvidia drivers got me back into X (with Beryl still running properly, even!).

However, grub died. It lost my WinXP Pro x64 boot option, and all my configurations were changed back to default. While i was updating, I saw nothing about grub being updated... just kernel stuff. What gives? How do I get my WinXP install to show up again? (I'll be searching the forums in the meantime.)

edit: I was using the same drivers, from the same repos as Camden and aidanr above me. Something else must be causing this problem...

edit2: Ok, a quick edit of /boot/grub/menu.lst got me back into business with Windows... even though i hardly use it anymore, its still a nice safety-net to have in case i majorly break something in linux (like tonight!)

```

title WinXP Pro x64
root (hd0,0)
savedefault
makeactive
chainloader +1

```

---

### Post by uriahs on 2006-12-14
Hello,

  I am having the prescribed problems. I have been unsuccessful with the specified commands.

  My xorg log says it can't find a bunch of font libraries, not sure if that could add to it?

  After trying various commands, some commads result in X sarting and displaying a black screen, others a white screen, sometimes a partially drawn (...'s in the middle of the screen, a weird white background, and some partially rendered weird white background) and a cursor! Other times if I start it from resuce mode (pressing Esc and option 2 at grub) it will boot looking like the old X with no gnome, and will partially render the bar which shows it's boot progress and play the nice start up sound.

  At the moment I am in a terminal, typing in lynx... this is quite painful... especially since I typed up this message before and accidentally pressed left and lost it :(

  If anyone has any advice on how to get into apretty graphical interface, or how to enable the Alt+F1 through F4 terminal switching, or anything else I would be much obliged

  For reference I am running the 3.18 kernel (I think) and I just tried down grading to the 7xxx nvidia drivers.

  Also this happend when I started watching a DVD it started rendering poorly (artifacts on the screen) and then really poorly (a lot more) then it locked up my computer, never recovered (completely irresponsive) and now i'm here, and really really need some help!

---

### Post by Rodneyck on 2006-12-14
Wow. It is unfortunate that the devs did not do more testing on different drivers and systems before releasing this.  Sorry, I know it is frustrating. I was in your shoes earlier.

Are you using an nvidia graphics card?  If so, the only quick-fix I can give you is to check our xorg.conf file and under "devices" make sure it does not say "nvidia" but "nv" instead. This will revert your graphic drivers back to the default ones that should allow you to at least boot into x server.

Good luck.

---

### Post by daller on 2006-12-14
Well the nvidia issues during a kernel upgrade is not a new issue?

(I've tried that more than 5 times...)

But I'm concerned about the GRUB error 17... My computer will not reboot before I take a backup...

---

### Post by aum11 on 2006-12-14
I offer this information for daller and any others who have had the error 17 problem.
I also had the error 17 immediately on rebooting after the updates this morning.  The  ext3 partition addresses were increased by 1.  At least two other folk would seem to have  had the same problem.

The story is at [http://ubuntuforums.org/showthread.php?t=318200](http://ubuntuforums.org/showthread.php?t=318200)

Hope this helps.

---

### Post by uriahs on 2006-12-14
Ahhh, that's how it's done. Well, i'm back in the GUI. However I did this, which I found on some forum:

sudo nano /etc/apt/sources.list
-- added the line "deb [http://www.albertomilone.com/drivers/unstable/edgy/32bit](http://www.albertomilone.com/drivers/unstable/edgy/32bit) binary/"
sudo aptitude update
sudo aptitude install linux-generic
sudo aptitude remove nvidia-glx-legacy
-- those were the drivers I was trying at the time
sudo aptitude install nvidia-glx
sudo nvidia-xconfig --composite
-- this got me into X but had heaps of artifacts (not sure if it was due to, unstable binaries or the --composite)
-- so I tryed
sudo nvidia-xconfig --no-composite
-- and it's a little better, either way, these commands "upgraded" me to 17-10-386 from generic, I now have two kernels... I think this would be a good time to move to 19/18 686 or something? And get rid of these beta drivers, and back to something more stable

---

### Post by RobertBln on 2006-12-14
It's not only about broken nvidia ...

This kernel panics here when trying to load "sata_promise". I had this issue when upgrading to edgy but it was fixed then. Now it's the same problem again as with the first kernel for edgy. 

I have a amd64 MSI K8T Neo2 - FIR (K8T800 Pro Chipset)

---

### Post by frolle on 2006-12-14
Should i reboot when i come home or should i just wait untill its fixed.. Hmm.. :) [-(

---

### Post by uriahs on 2006-12-14
Hrmmm, I have a SATA2 Promise card, and haven't had any problems.

frolle: If I were you, I wouldn't upgrade, or if it's already been done, start compiling a custom kernel. I didn't get to restart, it forced me to when everything graphically locked up.

---

### Post by RobertBln on 2006-12-14
Kernel panic (sata_promise) while booting: 

lspci |grep Promise
00:0d.0 RAID bus controller: Promise Technology, Inc. PDC20579 SATAII 150 IDE Controller (rev 02)

---

### Post by tophatandy on 2006-12-14
I have no problems after an update, from two days ago i think, with my Nvidia card. Everything is running smoothly.

---

### Post by tophatandy on 2006-12-14
quick question..

the update manager came up .. 

says i have a couple of updates i need to install..

one of them is: 

"linux-image-2.6 17-10-386"
it says its a linux kernal image..

as i said above i running an nvidia card....


do i update?

---

### Post by frolle on 2006-12-14
> **tophatandy said:**
> I have no problems after an update, from two days ago i think, with my Nvidia card. Everything is running smoothly.

Did you update your system last nigth?

---

### Post by tophatandy on 2006-12-14
updated from dapper to edgy either last night or the night before..

cant remember ..

**but** i am wondering if i take the kernel update..


i dont think i will...

---

### Post by uriahs on 2006-12-14
Well, the problem I had was with 2.6.17-10-generic, however if not compiled correctly, 386 might be at risk.

I'm running the 2.6.17-386 kernel at the moment, although I am compiling 2.6.19 at the moment and am going to move to that.

But it's up to you... at least you're armed with the knowledge of what it is, unlike the rest of us who got hit with it. Remember the problems aren't apparent until after you restart. Except in my case, but I think that was just rare and unfortunate.

---

### Post by tophatandy on 2006-12-14
so..


if I do install then it will ruin graphics on my system..


right?

---

### Post by shaft350x on 2006-12-14
It may possibly cause a conflict.  I updated (I have an Nvidia graphics card, and I've somewhat customized my Xorg.conf file) and I have not (cross-fingers) lost my GUI yet.  Although I haven't done any extensive testing.  I'm not sure if it has something to do with the AIGLX or something, because I haven't been able to get Beryl running properly yet, and either that is my misfunction with Beryl, or I don't have the beta drivers from Nvidia (although I did go through some walkthroughs to do this and have accelerated graphics).

I rebooted just to make sure, and I'm still good so far.  However, you may want to hold off until it gets sorted out for sure.

(Specs in my Sig)

---

### Post by jdong on 2006-12-14
> **RobertBln said:**
> It's not only about broken nvidia ...

This kernel panics here when trying to load "sata_promise". I had this issue when upgrading to edgy but it was fixed then. Now it's the same problem again as with the first kernel for edgy. 

I have a amd64 MSI K8T Neo2 - FIR (K8T800 Pro Chipset)

I didn't see anything in the the git tree for the kernel referencing any modification to the SATA/ATA bus.... I'm not 100% sure that was caused by a change to the kernel's behavior with this update.

---

### Post by Izobalax on 2006-12-14
OK, I've been redirected here after posting my problem in the Beginner's forum. So:

**History:**
OK, received a message last night (13/12/06) that I had system updates to download and install -- this included the kernel in question. So I duly updated and carried on with my stuff. 

**Problem:**
This morning, I boot the computer up and get to the log in screen. I notice that the display of the log in screen is a higher resolution that normal but think nothing of it. Insert username, then password. Log in screen goes away, then cursor disappears, screen goes black then a couple of seconds later my monitor displays this message:

"OVER FREQUENCY:

H: 95.2kHz V: 59.9Hz"

I deduced that my resolution was suddenly, without me doing anything, to high for my monitor to take, hence the monitor message. All this happened this morning. 

Today, I've just got in, tried the "sudo depmod -ae" command. Entered password, no activity for a bit and then the prompt reappears again. Rebooted machine, problem remains. I tried to reinstall the drivers by typing in the command suggested in the first post of this thread - no luck. 

I originally installed the nVidia drivers via downloading and running EasyUbuntu and checking the "nVidia drivers" option. 

Apart from all this, I really haven't got a clue what to do and if no-one can help me, I fear I may have to reinstall my machine *again* for the 3rd time in a week.

**Solution:**
Hopefully, this will come from one of you. 

What do I do, O' Knowledgeable and Wise Peoples of Ubuntu?

---

### Post by Pobega on 2006-12-14
I've got a question; Is there anyway to downgrade a kernel once you've upgraded? Or would you have to go back to a fresh install to do that?

---

### Post by n3Cre0 on 2006-12-14
I have an ati graphics card but nevertheless I aswell struggeled with yesterday's update.

It had overwritten my bootlist and appeared as GNU/Debian Linux instead of just Ubuntu...

Tryed to correct it by going into "recovery mode" (root shell without gui) but I got LOADS of error messages (like cannot start tty - bye bye shell) and got stuck so I had to force it to shutdown. Then booting from multiple livecds it appeared my partitions couldn't be found in /media or /mnt. Had to manually mount my partitions and then I copied my old bootlist over to /boot/grub/menu.lst. 
Then I went back to recovery mode that checked my disk and produced lots of text (appeared to be fixing some stuff). Next I tried to boot Ubuntu (gui) but got stuck again. After restoring an old xorg.conf I could lay my eyes again on a running Ubuntu...

3 kernel panics, many forced reboots, 4 livecds booted, 2 manual mount points, some backup files restored and 4 hours later it works.

Well it certainly was an experience ;)

---

### Post by PriceChild on 2006-12-14
> **Izobalax said:**
> What do I do, O' Knowledgeable and Wise Peoples of Ubuntu?This isn't a connected problem.

You need to reconfigure your xorg. Either by```
sudo dpkg--reconfigure xserver-xorg
```(answer default when unsure, space bar selects, enter continues)

You need to get to the part where you choose the monitors resolution. I reccomend you choose "Intermediate" level for selecting this,

Or if you know what you're doing, manually:```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by Izobalax on 2006-12-14
> **Pobega said:**
> I've got a question; Is there anyway to downgrade a kernel once you've upgraded? Or would you have to go back to a fresh install to do that?
I'm currently considering a fresh install right now ...

---

### Post by PriceChild on 2006-12-14
> **Izobalax said:**
> I'm currently considering a fresh install right now ...Go into synaptic.

Search for "linux-image" and select the current kernel image.

On the toolbar, "Packages>Force Version".

Choose the "(edgy)" instead of "(edgy-security)" and press ok. You may want to do the same with your linux-restricted-modules packages also.

then press apply.

Pricey

---

### Post by Suzan on 2006-12-14
This problem seems very weird!

I use the nvidia driver 9631 (installed with [envy](http://www.albertomilone.com/nvidia_scripts1.html)) and I use Beryl.

15 Minutes from now, I made all the updates (kernel, etc.) and restarted my machine. And what can I say: everything works very well, NO problems at all!

---

### Post by jdong on 2006-12-14
> **Suzan said:**
> This problem seems very weird!

I use the nvidia driver 9631 (installed with [envy](http://www.albertomilone.com/nvidia_scripts1.html)) and I use Beryl.

15 Minutes from now, I made all the updates (kernel, etc.) and restarted my machine. And what can I say: everything works very well, NO problems at all!

It is indeed very weird and it's no wonder QA/testing didn't catch it. A pretty small portion of our community has experienced some sort of breakage after upgrading, but everyone seems to have slightly different symptoms, and of the 5 or so people I've worked more closely with, after about 30 minutes of diagnosis we come up with a theory of how it happened, but no matter what we do, we are not able to reproduce it again. It's not nearly consistent enough to figure out the root cause and it's not rare enough to dismiss as a coincidence.

---

### Post by David Corrales on 2006-12-14
I just upgraded my machine and now, I can't even boot Edgy...

Error 15: File not found
Press any key to continue...

Considering that every other OS boots just fine from the same grub, I think it's a kernel problem.
I gotta thank the update for completely hosing my main machine and leaving it unusable. Way to go!

---

### Post by TheRingmaster on 2006-12-14
I have just updated my computer with the new kernel, rebooted, and all is well

---

### Post by tophatandy on 2006-12-14
> **Izobalax said:**
> Insert username, then password. Log in screen goes away, then cursor disappears, screen goes black then a couple of seconds later my monitor displays this message:

"OVER FREQUENCY:

H: 95.2kHz V: 59.9Hz"



used to have the exact same problem on one of my old computers..


no matter what it wouldnt go away.. 

thats all that would ever display..

even with a new monitor 

then i tried a new video card that worked for like a week,

after taking out the hard drive and wiping it, i would regain its video..
then lose it again.

got sick of the thing..

salvaged some parts..

then saved the rest for a boat anchor..

---

### Post by TheRingmaster on 2006-12-14
> **tophatandy said:**
> used to have the exact same problem on one of my old computers..


no matter what it wouldnt go away.. 

thats all that would ever display..

even with a new monitor 

then i tried a new video card that worked for like a week,

after taking out the hard drive and wiping it, i would regain its video..
then lose it again.

got sick of the thing..

salvaged some parts..

then saved the rest for a boat anchor..
good investment ;)

---

### Post by matchstich on 2006-12-14
just curious, i have a gforce in mine, and my system has started beeping today after the updates, had to restart a couple of times.  it beeps at start up, never used to.
could the beeping be caused by this update yall talking about.

---

### Post by matchstich on 2006-12-14
> **Rodneyck said:**
> Wow. It is unfortunate that the devs did not do more testing on different drivers and systems before releasing this.  Sorry, I know it is frustrating. I was in your shoes earlier.

Are you using an nvidia graphics card?  If so, the only quick-fix I can give you is to check our xorg.conf file and under "devices" make sure it does not say "nvidia" but "nv" instead. This will revert your graphic drivers back to the default ones that should allow you to at least boot into x server.

Good luck.
ok, but how do i do that? i dont know how to check anything on here, a complete newbie with linux,  i never did install any drivers for my gfroce 4000, it just worked when i installed ubuntu
thanks

---

### Post by Cariboo1938 on 2006-12-14
> **jdong said:**
> It is indeed very weird and it's no wonder QA/testing didn't catch it. A pretty small portion of our community has experienced some sort of breakage after upgrading, but everyone seems to have slightly different symptoms, and of the 5 or so people I've worked more closely with, after about 30 minutes of diagnosis we come up with a theory of how it happened, but no matter what we do, we are not able to reproduce it again. It's not nearly consistent enough to figure out the root cause and it's not rare enough to dismiss as a coincidence.Hi all,
I feel lost. As I have already posted here, I have trouble installing the newest nVIDIA driver on Edgy-64. I read this thread several times back and forth to figure out what I have to do, but I didn't grasp it yet. Maybe someone can help? I'm not certain about the state of my system after I did ```

sudo sh NVIDIA-Linux-x86_64-1.0-9631-pkg2.run 
```.
Is the new driver on the system? Do I just replace "nv" by "nvidia" in /etc/X11/xorg.conf? Do I need to install the new driver using 'envy'? Do I have to get the a newer version of the kernel? What is the current kernel right now? How would I do that? Unanswered questions all over the place! Maybe a good ''ubuntu soul'' is able to give me a hand! Thanks

---

### Post by LaneLester on 2006-12-14
What's the recommendation for those of us who haven't updated and don't want to lose our X? Wait for the next kernel update and hope the problem is gone?

Lane

---

### Post by David Corrales on 2006-12-14
> **David Corrales said:**
> I just upgraded my machine and now, I can't even boot Edgy...

Error 15: File not found
Press any key to continue...

Considering that every other OS boots just fine from the same grub, I think it's a kernel problem.
I gotta thank the update for completely hosing my main machine and leaving it unusable. Way to go!

I found the solution to my problem. Grub had incorrectly bumped up my root definition for all Ubuntu kernels (that's why the other ones booted correctly).
Instead of (in my case) **hd(0,4)**, I had **hd(1,4)**. The problem seems to be related with IDE/SATA mixed configurations.
In order to solve the problem, edit /boot/grub/menu.lst and change the root parameter to the correct setting.

---

### Post by cocotapioca on 2006-12-14
After the update, i cant even  boot!!
it cant fidn the file /lib/modules/2.6.17-10-386/module.dep.
I cant boot using the previuos image (2.6.15) now, there is some problem with /etc/mdadm/mdadm.conf.

---

### Post by Genican1 on 2006-12-14
I am running 6.10 band experienced a problem after upgrading earlier today.  All I got was the gnome panel.  No background, or desktop icons.  However, the "sudo depmod -ae" and a reboot fixed the problem.  Not sure if it's at all related, as I do not have an NVIDIA card, but i am running generic kernel.

---

### Post by jdong on 2006-12-14
> **Genican1 said:**
> I am running 6.10 band experienced a problem after upgrading earlier today.  All I got was the gnome panel.  No background, or desktop icons.  However, the "sudo depmod -ae" and a reboot fixed the problem.  Not sure if it's at all related, as I do not have an NVIDIA card, but i am running generic kernel.

That doesn't sound related...

---

### Post by Dragonfire on 2006-12-15
now could we fix the wireless systems and TI pcmcia controllers that were affected?

---

### Post by Dragonfire on 2006-12-15
> **matchstich said:**
> just curious, i have a gforce in mine, and my system has started beeping today after the updates, had to restart a couple of times.  it beeps at start up, never used to.
could the beeping be caused by this update yall talking about.



The beeping of which you speak is POST (power on self test) registering errors. look up the beep code errors, count the number of beeps. they correspond to an error code.

---

### Post by jdong on 2006-12-15
> **Dragonfire said:**
> now could we fix the wireless systems and TI pcmcia controllers that were affected?

*sputters incoherently* _what_ wireless systems and TI PCMCIA controllers affected?

And no, a software update can't feasibly cause the BIOS to fail POST (beeping at startup)

---

### Post by RobertBln on 2006-12-15
> **jdong said:**
> I didn't see anything in the the git tree for the kernel referencing any modification to the SATA/ATA bus.... I'm not 100% sure that was caused by a change to the kernel's behavior with this update.

Ah, ok, sorry, you are right - so downgrading linux-image wouldn't help. 

Workaround: After deleting sata_promise.ko (+update-initramfs) my system is running fine again (thank god there are no devices attached to it ... ). Upgrading the kernel to 2.6.19+ does also help but there is no 2.6.19 in edgy yet.

---

### Post by kleeman on 2006-12-15
> **jdong said:**
> I didn't see anything in the the git tree for the kernel referencing any modification to the SATA/ATA bus.... I'm not 100% sure that was caused by a change to the kernel's behavior with this update.

There was this listed in the changelog from upstream (a patch by Alan Cox related to sata  detection):

[http://lkml.org/lkml/2006/6/26/93](http://lkml.org/lkml/2006/6/26/93)

---

### Post by jdong on 2006-12-15
> **kleeman said:**
> There was this listed in the changelog from upstream (a patch by Alan Cox related to sata  detection):

[http://lkml.org/lkml/2006/6/26/93](http://lkml.org/lkml/2006/6/26/93)

That would change how drives are detected in terms of their capabilities (i.e. can I activate 33MB/s or 150MB/s speeds?) but I don't think it can cause sata_promise to panic on probe.


(I'm not a kernel developer, so dont quote me on this one!)

---

### Post by Rodneyck on 2006-12-15
Have the Kernel develpers or whoever is in charge re Ubuntu even posted anything on this?

---

### Post by jdong on 2006-12-15
No, they haven't.... nobody can reliably reproduce what happened here.

---

### Post by Izobalax on 2006-12-15
> **PriceChild said:**
> This isn't a connected problem.

You need to reconfigure your xorg. Either by```
sudo dpkg--reconfigure xserver-xorg
```(answer default when unsure, space bar selects, enter continues)

You need to get to the part where you choose the monitors resolution. I reccomend you choose "Intermediate" level for selecting this,
I'm afraid, PriceChild, that this didn't help me. In fact, it made matters worse, since Xorg somehow got confused and corrupted and I couldn't see the log in screen anymore. 

In anycase, I've reinstalled Ubuntu now to how it was and I've taken note as to which kernel this is, so that I can avoid it in future, just in case.

---

### Post by tbaac on 2006-12-15
Sorry, not actually a problem....... (edit)
I have an ASUS A6M laptop and have been running Edgy Kubuntu AMD64 bit since the last week or so of beta release.  I had to put noapic acpi=off into my grub file to get it to boot, but it has been fine up until recently.  Last night I turned on my laptop after being away from it for a few days and installed a bunch of stuff including the new kernel version (using Synaptic).  Now I can't get passed the initial 
"Starting up..... Decompressing linux done......Booting the kernel." message,
it just hangs there.  I booted using  a Kubuntu install disk and changed my graphics driver back to "vesa" from the installed nvidia one.  This made no difference.
Anyone have any idea?  Sorry, this may not have anything to do with the problem in this thread but I have the nvidia driver installed and after no problems for ages it suddenly won't boot so it seemed similar to start with although my symptoms are different.  Help please](*,) :-?

Somebody shoot me, sorry; the problem was that in installing the new kernel it removed the acpi=off noapic options from my grub.lst
I put them back and I can boot now.  (Its possible that I can update my bios, but there wasn't a newer one last time I checked).

Sorry.............................................

---

### Post by jdong on 2006-12-15
That doesn't seem similar to this issue though it's feasible that a kernel upgrade would cause it.

If you look at the grub menu item at bootup are noapic/nolapic still being applied?

---

### Post by tophatandy on 2006-12-15
so..


i am running open drivers for my nvidia card..


lets say i do take this update..

does it effect me?

:confused:

---

### Post by Dale61 on 2006-12-16
As a 'victim' of the previous faulty update, I'm certainly glad I checked the forums BEFORE going ahead with the update.

I can no longer afford to spend hours on end trying to fix something that ultimately isn't my doing.  Fortunately, my laptop has ATI graphics, so if worse came to worse, I have a backup to source a fix, but as I share my desktop pc, it's just not feasible to have it out of action for ANY amount of time.

I sympathise with anyone that has access to only one computer that has been affected by the latest 'update', and just hope any newby that has been affected isn't put off from using Ubuntu.

I have now adapted to the installed (occasionally problematic) kernel I am running, and at least I know how to fix this one when it goes belly up!

---

### Post by PriceChild on 2006-12-16
> **tophatandy said:**
> i am running open drivers for my nvidia card..

does it effect me?If you are running the open (nv in xorg.conf) then NO, you will definately not be affected.

---

### Post by bgoody on 2006-12-16
What about Nvidia 9629?

---

### Post by geokok1981 on 2006-12-16
Do u know how many users have been affected so far?
I myself, am waiting for a fix before updating the kernel. (nvidia-9629).

---

### Post by jdong on 2006-12-16
> **geokok1981 said:**
> Do u know how many users have been affected so far?
I myself, am waiting for a fix before updating the kernel. (nvidia-9629).

I've seen around 30 or so reports, compared to thousands after thousands back in the Dapper days.


As far as a "fix", nobody will be able to come up with one until somebody is able to reproduce this problem reliably.

As I've said before, I've worked pretty hard with those affected by the problem I could contact and attempted to identify a root cause and reproduce it consistently  by downgrading and re-performing the upgrade. However, nobody's been able to help me reproduce this more than just the initial incident.

---

### Post by olejorgen on 2006-12-16
Hm.. I think I was affected by this too. I had upgraded to 9631 drivers to get compiz up and running. The installation went fine, but when rebooting I got the dreadful x error screen. The strange thing is that I could fix the problem by reinstalling the 9631 driver and run startx. (I had to do this on each boot)

Obviously I got tired of this, so I ran sudo sh NVIDIA-Linux-x86-1.0-9631-pkg1.run --uninstall and reinstalled the official nvidia-glx package (and the restricted modules).

But when I try to run sudo nvidia-glx-config enable I get:
```

Error: unable to load nvidia kernel driver! Be sure to have installed
the nvidia driver for your running kernel.

```
Any clues?

EDIT: hm.. I edited xorg.conf myself and did a sudo modprobe nvidia and now everything seem to be fine... strange

---

### Post by Cariboo1938 on 2006-12-16
> **jdong said:**
>  
As far as a "fix", nobody will be able to come up with one until somebody is able to reproduce this problem reliably.
As I've said before, I've worked pretty hard with those affected by the problem I could contact and attempted to identify a root cause and reproduce it consistently  by downgrading and re-performing the upgrade. However, nobody's been able to help me reproduce this more than just the initial incident.
On page #21 of this thread I already posted what happened on my computer when I tried to install the newest nvidia driver, for which I downloaded the package NVIDIA-Linux-x86_64-1.0-9631-pkg2 and used ```
sudo sh NVIDIA-Linux-x86_64-1.0-9631-pkg2.run 
``` to install it.
After this command, is there a new driver on my computer? 
So, what you are recommending here is,  just to repeat the installation again? Do I have to uninstall a driver first? In case I lose xserver again and only have a black screen with the user prompt, what would be an effective way to trace the error? Is the information in /var/log/Xorg.0.log enough?
I  appreciate any reply, 
Thanks
Cariboo

---

### Post by missmoondog on 2006-12-16
nope, not as widespread for me this time either but only because i only have 2 machines with nvidia in them. both have gone south now! last time it effected all 7 machines. these were my 2 "extra" machines that i still had ubuntu on, but not anymore. these rediculously foobarred updates in ubuntu are to much. i'm now hanging the zenwalk 4.0 hat on ALL my machines. while this is a super forum for finding the quick fix to these things, they just occur to often for me.

more often than winblows foobarred updates even!!

---

### Post by Ted D. on 2006-12-16
I don't know about nvidia cards. I don't have one, but highest resolution I can now get is 832x624. What has happened (using dapper)?. I this a coincidence and not related to the latest updates or has it something to do with the latest updates?
Ted D.

---

### Post by Kevincol on 2006-12-17
I am running dapper with original drivers and cannot get past the loggin checks.  Apparantly the faultis in /hda1 node1308737.   It has an imagic flag set.   The computer tells me to run fsch manually which is a bit beyond my capabilities.   Would it be best to do a fresh install (yuk)?
Up until this upgrade I have been very happy with Ubuntu.
Kevin

---

### Post by captain.kipper on 2006-12-17
> **edu65 said:**
> Hi,

I have both the 686 and the 386 kernel and I have just updated both. I am using the stock nvidia-glx-1.0.8776 driver. The strange thing is that rebooting into the 686 kernel is fine, whereas the 386 kernel yields the problem described in this thread. I am using Dapper.


I have found the same X problem after upgrade, but only in the 383 kernel ( and at least one other post in this thread also finds this). 

My advice - try restarting and using the **generic** kernel in the boot options (this is anyway the preferred one if you have a PC that isn't ancient).

Is there anyone so far that has reported this nvidia fault when booting into the generic kernel?

---

### Post by Indefinity on 2006-12-17
I'm fairly new to Ubuntu (just started, and essentially crashed, Ubuntu yesterday), so I don't know too much of the technical side of things. However, while looking at the xorg.conf file in VIM, I noticed the following information:
```

Secion "Device"
    Identifier "ATI Technologies, Inc. Radeon RV100 QY [Radeon 7000/VE]"
    Driver "nvidia"

...

Section "Screen"
    Device "ATI Technologies, Inc. Radeon RV100 QY [Radeon 7000/VE]"

```

Any reason why it would think that my card was an ATI card now? Would rewriting this as an NVidia card fix the problem? I have a GeForce 7900 GS card, but I'm not sure what to type exactly for the identifier and device...

EDIT: I forgot to mention that all modes had a resolution max of only 1024x768, while I had Ubuntu working with a resolution of 1680x1050 before the update.

---

### Post by kamei on 2006-12-18
Mod: Please delete this post.

---

### Post by Skat on 2006-12-18
hi, when I type this

```
sudo apt-get install --reinstall linux-restricted-modules-`uname -r` nvidia-glx
```

it says that the linux-restricted-modules-...  package is not found..

can anyone tell me which repository should I activate? and how?

xwindows stay in a blank screen after logging in.  In fact, it shows the background image of the login prompt, but it stays there. It broke down after updating kernel.

thanks

---

### Post by Skat on 2006-12-18
> **jdong said:**
> 

If you've applied the updates and rebooted and you can get to a graphical login prompt, **you are not affected by this issue.**.



after reading your message once again I noticed that this is my situation.  I've looked for a solution in the ubutuforums but I was not able to find one.  Do you have any suggestions?

Thank you very much
Skat

---

### Post by geokok1981 on 2006-12-18
Ok I just did the update (got sick of seeing the notification for updates).
Everything is fine (I use nvidia 9629). Lucky me... :)

Just one question. I thought that after a kernel update I had to re-install nvidia drivers.
However, nvidia settings from the menu was working and glxinfo said:
direct rendering: yes

So, do I or dont I have to re-install nvidia drivers when upgrading the kernel??
(I did re-install this time just to be sure but would like to know for future upgrades)

---

### Post by chadk on 2006-12-18
I'm having a problem with my nvidia onboard NIC, not the video... but it seems related to this Dec 13 thing as that's when it first cropped up.

---

### Post by bkeithly on 2006-12-18
The upgrade seems to have effected my video and wifi as well.

HP 6040dv, installed 6.10 64adm twice.  

Got wifi working with ndiswrapper both times.  As soon as I performed all updates and rebooted, system will not connect to WIFI network.

Re-installed all WIFI related software still no change.  

Anyone feel this could be related to the nvidia issues?

---

### Post by gerick on 2006-12-19
> **geokok1981 said:**
> Ok I just did the update (got sick of seeing the notification for updates).
Everything is fine (I use nvidia 9629). Lucky me... :)

Just one question. I thought that after a kernel update I had to re-install nvidia drivers.
However, nvidia settings from the menu was working and glxinfo said:
direct rendering: yes

So, do I or dont I have to re-install nvidia drivers when upgrading the kernel??
(I did re-install this time just to be sure but would like to know for future upgrades)

Ditto: I bit the bullet and let the updates install, expecting to have to reinstall the nvidia drivers.  Rebooted after the updates, crossed my fingers, and X started up and loaded KDE.  glxinfo shows direct rendering.  I did not reinstall nvidia.  Currently running nvidia 9631.

Maybe because this is a upgrade to the kernel, not a new kernel?  I noticed that grub did not put another menu option like it does sometimes.

---

### Post by Cariboo1938 on 2006-12-20
> **jdong said:**
>  
 ......
**Solutions and Workarounds**
 If you installed nvidia drivers from an executable downloaded from nvidia.com, please follow the instructions for installing that driver again.
 .....
On behalf of everyone here at Ubuntu, I apologize for any inconvenience this may have caused you.Help please...
I tried to follow the above instructions without success yet. The nvidia installer log > nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Wed Dec 20 09:02:28 2006

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  precompiled interfaces  : true
  no ncurses color        : false
  query latest version    : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no recursion            : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  no kernel module        : false
  force SELinux           : default
  no X server check       : false
  force tls               : (not specified)
  force compat32 tls      : (not specified)
  X install prefix        : (not specified)
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
  compat32 install chroot : (not specified)
  compat32 install prefix : (not specified)
  compat32 install libdir : (not specified)
  utility install prefix  : (not specified)
  utility install libdir  : (not specified)
  doc install prefix      : (not specified)
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : [ftp://download.nvidia.com](ftp://download.nvidia.com)
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> The file '/tmp/.X0-lock' exists and appears to contain the process ID '4195'
   of a runnning X server.
ERROR: You appear to be running an X server; please exit X before installing. 
       For further details, please see the section INSTALLING THE NVIDIA DRIVER
       in the README available on the Linux driver download page at
       [www.nvidia.com](www.nvidia.com).
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).
tells what is wrong but I don't know what to do. What are all these "false" and "not specified" messages?How can I exit X? Please help!

---

### Post by Roque on 2006-12-20
Press Ctrl-Alt-F1 
Then write:
```

/etc/init.d/gdm stop

```

And then run the nvidia installer again.

---

### Post by Cariboo1938 on 2006-12-20
> **Roque said:**
> Press Ctrl-Alt-F1 
Then write:
```

/etc/init.d/gdm stop

```
And then run the nvidia installer again.Thanks for the hint. Unfortunately I still couldn't install 'nvidia'.
During the installation I got several Warnings, for example: > You appear to be using a modular X.Org release, but nvidia-installer was unable to determine the correct xlibrary installation path with the 'pkg-config' utility. Please install the X.Org SDK/developpment package for your distribution. Although, the installer finished with the message '...successfully installed'. After reboot xserver didn't start. I edited "/etc/X11/xorg.conf"  replacing "nvidia" by "nv" and then the xserver started again. Any ideas what I'm doing wrong? I appreciate any reply!

---

### Post by Dale61 on 2006-12-20
Firstly, what release does this problem affect?  Dapper or Edgy or both?  The heading certainly doesn't give us that info.

Secondly, therefore, having read through ALL the posts, I am still not 100% certain if this problem will affect me (Dapper), so I've been holding off upgrading my kernel (it's still waiting to be downloaded in my Update Manager).

I'm finding that since the release of Edgy, these forums are becoming more difficult to navigate, and more importantly, more difficult to get an answer.

Is there any way of putting all the Edgy questions into it's own Edgy forum, and do the same for Dapper?

I still run Dapper, and I posted a question a couple of days ago, but with all the Edgy problems that needed answers, my question was quickly swept off the first page and I found it hidden deep in page three.  This happened within a few hours.

---

### Post by Cariboo1938 on 2006-12-21
> **Dale61 said:**
> Firstly, what release does this problem affect?  Dapper or Edgy or both?  The heading certainly doesn't give us that info.......In my case... I'm running Edgy-amd64!

---

### Post by kleeman on 2006-12-21
> **Cariboo1938 said:**
> Thanks for the hint. Unfortunately I still couldn't install 'nvidia'.
During the installation I got several Warnings, for example:  Although, the installer finished with the message '...successfully installed'. After reboot xserver didn't start. I edited "/etc/X11/xorg.conf"  replacing "nvidia" by "nv" and then the xserver started again. Any ideas what I'm doing wrong? I appreciate any reply!
Try
sudo apt-get install xserver-xorg-dev

and then run the nvidia installer again

---

### Post by Katryx on 2006-12-21
kernel: 2.6.17-10-386

I installed 9631 using Method 2 from [this guide](http://ubuntuforums.org/showthread.php?p=1645708) (and I was going to post this in that thread but got tabs mixed up <_<).  This error is displayed when attempting to start GDM:

> X: cannot stat /etc/X11/X (No such file or directory), aborting.

---

### Post by kleeman on 2006-12-21
Sounds like some of your linked files in X are broken for some reason (a bit worrying that). I have that file and it is linked to /usr/bin/Xorg so you could try
sudo ln -s /usr/bin/Xorg  /etc/X11/X
and see whether things work

---

### Post by Katryx on 2006-12-21
> **kleeman said:**
> Sounds like some of your linked files in X are broken for some reason (a bit worrying that). I have that file and it is linked to /usr/bin/Xorg so you could try
sudo ln -s /usr/bin/Xorg  /etc/X11/X
and see whether things work

"/etc/X11/X is not executable
YPE"

There is no Xorg in /usr/bin, but there is an X11, and inside that there is an X.  So I unlinked the link to /usr/bin/Xorg and replaced it with this:
```
sudo ln -s /usr/bin/X11/X /etc/X11/X
```
Now receiving this error at restart of GDM:
"X: /etc/X11/X points back to X wrapper executable, aborting."

---

### Post by Indefinity on 2006-12-21
Just changing the driver back to nv doesn't change anything. My entire xorg.conf file seems to be changed. See my post before about my device appearing to be an ATI card instead of an NVidia.


EDIT: Woot I got the GUI working again. Upon looking at the error log file closely, I found it was looking for the video device at 1:0:0. However, in the xorg.conf file, the video device (in my case, "GeForce Go 7900 GS") was set at```
BusID "PCI:0:1:0"
```
I simply changed the "0:1:0" to 1:0:0" and I got my GUI back. However, my resolution only goes up to a max of 1024x768... I changed the resolution values in the xorg.conf file, but that didn't seem to do it. Any ideas?

---

### Post by tophatandy on 2006-12-21
well..

after trying to install the drivers on my old computer (now my brothers) I lost all graphics on my system.. not even a prompt..

so I went into safe mode and typed
```
sudo dpkg-reconfigure xserver-xorg
```
then I took all the defaults and reset my system back to the nv driver and everything is back to normal.. even though I would still like hardware exceleration..

the card was a GeForce4 440 agp 8x

hope that helps..

---

### Post by kleeman on 2006-12-21
> **Katryx said:**
> "/etc/X11/X is not executable
YPE"

There is no Xorg in /usr/bin, but there is an X11, and inside that there is an X.  So I unlinked the link to /usr/bin/Xorg and replaced it with this:
```
sudo ln -s /usr/bin/X11/X /etc/X11/X
```
Now receiving this error at restart of GDM:
"X: /etc/X11/X points back to X wrapper executable, aborting."
It sounds to me like your X system is borked. The file /usr/bin/Xorg is listed at the Ubuntu packages site as being in the package xserver-xorg-core which is a vital part of X. Do you have it installed? Look using synaptic. If you do try reinstalling it.

---

### Post by Cariboo1938 on 2006-12-21
> **kleeman said:**
> Try
sudo apt-get install xserver-xorg-dev
and then run the nvidia installer againHi kleeman and thank you so much for offering help! 
I followed your instructions and noticed some improvement compared to earlier tries. The warnings during running NVIDIA-Installer are reduced to one> **myself]Warning: Unable to perform the runtime configuration check for libraryl 'libGL.so.1' ('/usr/lib32/libGL.so.1.0-9631') said:**
> After that followed the Question if I want to run the nvidia xconfig utility to update my X configuration so that the NVIDIA X Driver will be used at restart which I answered with 'YES'. After reboot though x server didn't start. Instead I got the X Server output information[QUOTE=myself]X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Rev.0, Release 7.1.1
Build Operating System: Linux 2.6.15-7 x86_64
Current OS: Linux BitByter 2.6.17-10-generic #2 SMP Tue 5 21`:16:35 UTC 2006 x86_64
Build DAte: 07 July 2006 I can tell you, the whole nVIDIA driver update turned out to be a nightmare for me:confused: . Is there another way to do it?

---

### Post by Katryx on 2006-12-22
> **kleeman said:**
> It sounds to me like your X system is borked. The file /usr/bin/Xorg is listed at the Ubuntu packages site as being in the package xserver-xorg-core which is a vital part of X. Do you have it installed? Look using synaptic. If you do try reinstalling it.

Thank you. :) That seems to've fixed X.

But, as soon as GDM is entered, the drums sound plays and the screen is blank aside from the monitor's little "Out of Range" message in the center.  I'm guessing this is because xorg.conf contains resolutions that are far too high for the monitor, so I reentered the command line to edit that.  Entered username and password, works fine, Ubuntu info displays...then nothing.  No command line to type anything into. o_O Just stops after "Ubuntu comes with absolutely no warranty, to the extent permitted by applicable law."

---

### Post by kleeman on 2006-12-22
> **Katryx said:**
> Thank you. :) That seems to've fixed X.

But, as soon as GDM is entered, the drums sound plays and the screen is blank aside from the monitor's little "Out of Range" message in the center.  I'm guessing this is because xorg.conf contains resolutions that are far too high for the monitor, so I reentered the command line to edit that.  Entered username and password, works fine, Ubuntu info displays...then nothing.  No command line to type anything into. o_O Just stops after "Ubuntu comes with absolutely no warranty, to the extent permitted by applicable law."
Sounds like something is chewing up a ton of resources so it is taking ages to get to the command line. Reboot in recovery mode (should be an option on your grub menu) and reedit /etc/X11/xorg.conf. If that does not work personally I would reinstall but keep the home partition. It doesn't take all that long and you have most of your old stuff still.

---

### Post by Skerit on 2006-12-27
This is one messy bug... Ever since it came up I had to reinstall those kernel modules every time I booted... I've used every repo possible... Ugh, it's such a long story, but this is an ugly bug!

---

### Post by rolando2424 on 2006-12-27
I also had the same problem, with Dapper, but I don't remember upgrading anything, I tougth that it was the Webcam that caused the problem.

But I also was waiting for an excuse to upgrade to Edgy, so I didn't give much tought :D

---

### Post by LaneLester on 2006-12-27
> **Skerit said:**
> This is one messy bug... Ever since it came up I had to reinstall those kernel modules every time I booted... I've used every repo possible... Ugh, it's such a long story, but this is an ugly bug!

I'm glad I learned about this before upgrading to x.34. I'm sticking with x.33, in hopes that x.35 will be decent. :???: 

Lane

---

### Post by alan yeates on 2006-12-30
> **tophatandy said:**
> well..

after trying to install the drivers on my old computer (now my brothers) I lost all graphics on my system.. not even a prompt..

so I went into safe mode and typed
```
sudo dpkg-reconfigure xserver-xorg
```
then I took all the defaults and reset my system back to the nv driver and everything is back to normal.. even though I would still like hardware exceleration..

the card was a GeForce4 440 agp 8x

hope that helps..

just what I did, but checked the NVidia site and found that my GeForce 4 mx440 is supported with the new driver and not a legacy issue. Tried again and after a couple of reboots all was well. I do see a prob for new users in not knowing what is an old card and what isn't, suggest a better explanation in the software updates box!:-D - also I have only just realised that any new kernel may mean going through this all again,so do it on a good day!

---

### Post by ERegoS on 2006-12-31
Just installed 6.10 and got the "No screens found" issue (new install, migrating from SuSE 10.1).

I have a Leadtek Winfast 3D S325, TNT/M64 32Mb which (after some Googling) turns out to be NVIDIA compliant :( . Problem occurred when **using a Compaq TFT5010 monitor**, which turned out to be significant.

By now, I succeeded to finalize the installation and run Ubuntu; **I solved it  when using a CRT-monitor**. And currently it is a 100% monitor dependent problem: with CRT it works, with TFT it doesn't.
It gets worse: starting up with CRT works fine and after that switching live to TFT remains working.

To me that indicates that this is not just a driver / video-card issue. But there are probably more experienced users out there that can comment? Anything more from my side would be purely speculating.

---

### Post by Cariboo1938 on 2006-12-31
My file "xorg.conf" tells me that I have the graphic driver "nv" installed.
> EndSection
Section "Device"
    Identifier     "NVIDIA Corporation NV34 [GeForce FX 5200]"
    Driver         "nv"
EndSection
Section "Screen"I tried to use Automatix2 to install a new nvidia driver and got the following warning:> Automatix has detected that the correct nVidia driver is either correctly installed or you are attempting to overwrite an existing driver installation. This is NOT recommended.If you still want to continue hit YES, or else hit NO to resume with the rest of the options chosen.Now I'm confused:confused:  and don't know how to check which driver is installed?

---

### Post by tophatandy on 2006-12-31
so cariboo.. what do you get when you boot up?

do you actually get graphics or text or what?

---

### Post by Papou on 2007-01-03
A description of what appen here , in case that could help to understand where the bug comes from :

Hardware = Athlon XP  with Nvidia FX5200.
I have 2 installed kernels : -386 and -generic , and I run usually the -386  
I use Nvidia drivers 1.0.8776 from official repository.

After upgrade 2.6.17-10.33 to .34, the x server was still OK with the -386 kernel , but no more with the -generic :  failed to load NVIDIA kernel module.

Replacing device driver nvidia by nv in xorg.conf allow X server to work  without direct rendering.   

Back to nvidia driver, issue was solved by reloading linux-restricted-modules-....-generic.

Good luck to the bug fixer ;) 

Serge.

---

### Post by Cariboo1938 on 2007-01-03
> **tophatandy said:**
> so cariboo.. what do you get when you boot up?

do you actually get graphics or text or what?

I get text...no graphics!

The story goes like this:
In the first place I downloaded from [www.nvidia](www.nvidia) the driver NVIDIA-Linux-x86_64-1.0-9631-pkg2.run and installed it manually. 
During this procedure I get a warning: 
"Unable to perform the runtime configuration check for library 'libGL.so.1 (/usr/lib32/libGL.so.1.0-9631') assuming successful installation." 
and also I was asked: 
"Would you like to run the nvidia-xconfig utility to update your Xconfiguration so that NVIDIA Xdriver will be used when you restart?" 
Here I answered YES. 
After that I got the message: 
"your Xconfiguration file has been successfully updated. Installation of the NVIDIA Accelerated Graphics Driver for Lunix x86_64 is now complete"

I restarted the computer and after the Ubuntu boot splash I get a black screen with a blue text box with white text saying:
[COLOR="Red"]"Failed to start the X server. It's likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?"[/COLOR]
 
Answering yes gives the following info:
[COLOR="Red"]"X Window System Version 7.1.1
Release date: 12 May 2006
X protocol version 11, Rev.0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 x86-64
Current OS: Linux Bitbyter 2.6.17-10 generic #2
SMP Fri Oct 13 15:34 UTC 2006 x86_64
....
The X server is now disabled. Restart GDM when it is configured properly"[/COLOR]

Log file /var/log/Xorg.0.logsays:
[COLOR="Red"]"Failed to initialize the NVIDIA kernel module!
Please ensure that there is a supported NVIDIA GPU in this system and that the NVIDIA device files have been created properly"[/COLOR]

I used ```
sudo sh NVIDIA-Linux-x86_64-1.0-9631-pkg2.run --uninstall
``` to remove the installation and then I tried also to install nvidia drivers with Automatix. Here I got the message:
[COLOR="Red"]"Automatix has detected that the correct nVidia driver is either correctly installed or you are attempting to overwrite an existing driver installation. This is NOT recommended. If you still want to continue .... "[/COLOR] I answered NO and canceled Automatix.

If I do a search I get: 

> root@BitByter:~# sudo find / -name nvidia.*
/lib/linux-restricted-modules/2.6.17-10-generic/nvidia_backup/nvidia.mod.o
/lib/linux-restricted-modules/2.6.17-10-generic/nvidia_legacy_backup/nvidia.mod.o

That's all of the nvidia installation I can find! 


I have no idea what to do with this kind of information!
Maybe somebody understands what it means and offers me help.](*,)

---

### Post by tophatandy on 2007-01-04
are you using an lcd.. some people suggest it might just be the monitor.. try a crt if it is possible..

if not, try to return your system to using the open source driver

I used this code and took all the defaults to restore my system.. i did this in reovery mode which i acessed from the grub menu.

```
sudo dpkg-reconfigure xserver-xorg
```

hope this helped..

post if it worked.

=]

---

### Post by greatgoo on 2007-01-04
I am a bit late coming to this discussion.  I installed Edgy from the iso burned to a cd.  The distribution worked fine.  I then installed the updates, (83 of them as I recall) from the Ubuntu site.  I got the black screen.  There seems to be a shift in the video right at the end.

Yesterday I went looking in the logs and found the server is timing out when initializing.

I ran the command line reconfig found in xorg.conf and got the machine to run via vesa, but it is clunky.

This is my linux learning workstation and I am more than happy to wipe, reinstall and apply the updates again to replicate the issue of that will help.

David Davis
Toledo, OR 97391

---

### Post by Cariboo1938 on 2007-01-04
> **tophatandy said:**
> are you using an lcd.. some people suggest it might just be the monitor.. try a crt if it is possible..Thanks tophatandy for this hint...I do only use a LG FLATRON T710BH crt monitor already.
 
> **tophatandy said:**
> 
I used this code and took all the defaults to restore my system.. i did this in recovery mode which i accessed from the grub menu.

```
sudo dpkg-reconfigure xserver-xorg
```

hope this helped..

post if it worked.

=]
Yes this works. I used that too to get back to normal, i.e. I reinstalled the driver 'nv'.

---

### Post by Cariboo1938 on 2007-01-04
I gave up the idea to install NVidia driver version 9631 on Edgy Eft. 
Instead I used ```
sudo apt-get install --reinstall linux-restricted-modules-`uname -r` nvidia-glx
```to install nvidia drivers. 
I also had to edit /etc/X11/xorg.conf where I replaced "nv" by "nvidia". 
After reboot, during a split of a second I saw the nVidia  Logo and after that the X server started. 
For now I declare my case closed!
I wonder how I could check which driver version I have installed now? Is there an upgrade possible for newer driver versions?:-k

---

### Post by tophatandy on 2007-01-04
you can check the repositories for an app called "hard info".. then go to the display section and check to see who your drivers were compiled by (vendor) .. if its the open it was by  x.org foundation or if it was the nvidia driver it should say nvidia..

i think.. i dont know.. kind of new to ubuntu but have had some formal linux background.. (most of that was for servers and whatnot though)

---

### Post by B()X_BREAKER on 2007-01-05
I have been fighting with this same problem for a few days now. In my case the error says it is still trying to load the older kernel driver and the nvidia drivers I installed with automatix2 bleeder. I have been able to kill it, restore the original xorg.conf, kill it again, reload nvidia xorg.conf, and some how make it work. But this is lost when I reboot. I even tried blacklisting the nv driver but that made things worse. Now I can't even get my nvidia xorg to work at all even after taking nv off the blacklist. I don't know if depmod -ae is doing anything but I try it about every other time reloading xorg's.

So I guess my next step is to ask if anyone knows how I go about either
A: Killing the old kernel drivers
or
B: Maybe recompiling the new drivers to replace the old ones completely?:confused: 

I probably don't know what I am talking about but it seems to be the next step to try from my viewpoint.  If I can pin down exactly what steps worked when reloading xorg files may a script would be a temporary fix. I don't need help getting back up and working with regular drivers, I just want to hack at a fix to play with the latest drivers.

---

### Post by Jongi on 2007-01-07
> **PriceChild said:**
> Have you got nvidia-glx installed?

If not, then follow [http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)

This did the trick for me

---

### Post by marcus2004 on 2007-01-11
I am not sure if this is what is affecting me or not. Every time I update the kernel I cannot boot into X after. I have been running the envy script off this site:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
This reinstalls the newest nvidia drivers (I believe). I am not sure if I should be doing this or if there is a better way.

---

### Post by iblicf on 2007-01-12
does the problem been fixed ? 

i have just reinstall the ubuntu to edgy , after  sudo apt-get install nvidia-glx , then got trouble 
use sudo apt-get install --reinstall linux-restricted-modules-`uname -r` nvidia-glx
        sudo depmod -ae  
        still not working , wha't can i do ? wait the rep to update ? 

by the way ,   my mplayer can't ajust the brightness or the contrast using 1,2,3,4 num key before (  hardware accelerate  ) i don't know what's wrong ,does anybody got the same problem ?

---

### Post by kbarrett on 2007-01-14
> **marcus2004 said:**
> I am not sure if this is what is affecting me or not. Every time I update the kernel I cannot boot into X after. I have been running the envy script off this site:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
This reinstalls the newest nvidia drivers (I believe). I am not sure if I should be doing this or if there is a better way.

I had the same problem.

The problem here is with the latest nvidia beta driver. If you use the latest beta envy script, you will keep re-installing that beta driver.

remove the current driver:
sudo apt-get --purge remove nvidia-glx

reset xorg to "nv" so xwindow works again:
sudo dpkg-reconfigure -phigh xserver-xorg

Remove envy, and then load the stable version of envy. Use the stable version of envy to load the ubuntu officially supported nvidia driver.

---

### Post by LaneLester on 2007-01-15
After trying unsuccessfully beryl, compiz, and two monitors, things were messed up to the point that I did a fresh reinstall of Ubuntu. This gave me the opportunity of updating to the kernel headers I had been avoiding due to this thread.

I then used the instructions at this site:
[http://albertomilone.com/latest_nvidia_udsf_edgy.html]("http://albertomilone.com/latest_nvidia_udsf_edgy.html")
to install the driver for my nVidia 5500.

All is well now with metacity and two monitors. I think I'll leave compiz and beryl alone for now.

Lane

---

### Post by darrenrxm on 2007-01-16
Thank you for posting information on how to fix this, Works like a charm.

---

### Post by DKnight768 on 2007-01-16
Hello.
I had NVidia BETA drivers installed (from Alberto Milone's repository, as described in the Unofficial Starter Guide), and after the kernel update they stopped working. ](*,) 
I uninstalled the nvidia-glx package, and proceed to reinstall it, but apt reported a broken dependency (nvidia-kernel.9760?).:-k 
This is how I solved it:

```
sudo apt-get remove nvidia*
sudo apt-get install linux-restricted-modules-`uname -r`
```
Downloaded _[envy]("http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.8.1-0ubuntu1_all.deb")_ and used it to reinstall the driver (painless process)

And now I have full 3D acceleration again (working Beryl and Cedega).

Hope this help someone.;)

---

### Post by OmniDistortion on 2007-01-19
Okay my friend is unable to get into his terminal and what appears is a blank screen which you can type in after X crashes, but it's not a terminal. How do we access the terminal after this happens, or while booting up?

---

### Post by kleeman on 2007-01-20
Try

ctl-alt-f1

---

### Post by shk on 2007-01-21
has anyone found the solution to this problem ? i am running edgy with the nvidia 9625 driver, and everytime i reboot, i get the "No screens found" problem. I have to kill gdm , reinstall the nvidia driver (with the nvidia installer), and then start gdm again. Luckly i don't reboot very often, but sometimes power fluctoations occur and the computer restarts. This is very frustrating ](*,)

---

### Post by olejorgen on 2007-01-22
> **shk said:**
> has anyone found the solution to this problem ? i am running edgy with the nvidia 9625 driver, and everytime i reboot, i get the "No screens found" problem. I have to kill gdm , reinstall the nvidia driver (with the nvidia installer), and then start gdm again. Luckly i don't reboot very often, but sometimes power fluctoations occur and the computer restarts. This is very frustrating ](*,)

I might have had the same problem as you. My solution was to uninstall everything of nvidia drivers, reboot with nv driver and install the driver from the repos.

---

### Post by Big-Wayne on 2007-01-23
Had the same problem myself, solved using the script from here;
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

[img]http://www.ubuntuforums.org/attachment.php?attachmentid=23694&stc=1&d=1169550223[/img]

---

### Post by lopoetve on 2007-01-25
> **olejorgen said:**
> I might have had the same problem as you. My solution was to uninstall everything of nvidia drivers, reboot with nv driver and install the driver from the repos.

What's the best way to do this?

---

### Post by bzanelli on 2007-02-02
Any news on that?

I've just downloaded a fresh 6.10 and I'm having the same problems :( 

Already tried almost every tip I found... none worked :( :(

---

### Post by bsprowl on 2007-02-08
I've got this problem.  Asus A8N-E mother board, MSI GeForce PCI-E 6600 w/ 128 MB, new Edgy install that worked until I installed the updates.

The fix on the first page got everything working except the acceleration.  

Still looking for a fix.

Bob

---

### Post by DarkStarAeon on 2007-02-10
1. This issue severely freaked me out, severely uncool, can't believe that there was no warning when installing the updates. This is a kind of problem I would expect from Microsoft, not Ubuntu.

2. None of any of the "fixes" here worked for me.

3. Thank God I finally remembered that I had used Envy to install and configure my Nvidia driver, once I remembered that, all I had to do was type "envy" in the command line and it fixed this whole mess for me.

4. I am still shocked about this, I understand having to reinstall a driver with a kernal upgrade, but geesh, a little warning would have been cool. It's free software sure, but still.

---

### Post by daller on 2007-02-11
To all of you having problems with 6.10 - Go for 7.04!

It's running nice on all of the 12 (or so...) machines I've installed it on so far!

Sad to hear that this issue still stands!

---

