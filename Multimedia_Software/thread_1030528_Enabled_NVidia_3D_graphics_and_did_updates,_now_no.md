---
title: "Enabled NVidia 3D graphics and did updates, now no video"
date: 2009-01-04
forum: Multimedia Software
---

### Post by DKAudio on 2009-01-04
Computer is a Toshiba Satellite Pro 6100
P4
40GB HDD
1G PC2100
Nvidia Graphics^n card

I did updates and then tried to enable 3D graphics (I came accross a website explaining how to do it).  I went to Hardware Drivers and then clicked enable for Nvidia.  Upon re-boot I get the Ubuntu loading screen but when it is supposed to get to where I log in the screen is messed up.  All I can say is it resembles clouds and eventually fades to an off white.  

I assume this happened when I enabled the 3D graphics and my video card cannot support it?  How can this be fixed?  I am new at Ubuntu so please explain things well.

The reason I did this in the first place was because when I stream video (youtube or similar) it is very choppy and skips up to 10 seconds at a time.

Thanks

Dan

---

### Post by cariboo on 2009-01-04
It would help if you gaves us some more information

> Nvidia Graphics^n card

doesn't tell us much, if you don't know what model of Nvidia card you have in a Applications-->Accessories-->Terminal type:

```
lspci | grep VGA
```

and paste the output in your next post.

Jim

---

### Post by DKAudio on 2009-01-04
I can't get into Ubuntu, that is the problem, I see absolutely nothing on my screen.

The last thing I can see is the part when the screen is black and it says Ubuntu with the orange load bar (after POST but before log-in).

---

### Post by DKAudio on 2009-01-05
Bump

---

### Post by DKAudio on 2009-01-07
Maybe this will help... 

The following is the website with the tutorial I followed before my video went away, again, I assume that my video is now bad in Ubuntu because my graphics card cannot handle 3D graphics, I just want to get it back the way it was (Remember I get a white "foggy" screen where the log in would normally be, I cannot visually get into the OS).

[http://www.howtoforge.com/compiz-fusion-ubuntu-8.04-nvidia-geforce-fx-5200](http://www.howtoforge.com/compiz-fusion-ubuntu-8.04-nvidia-geforce-fx-5200)

---

### Post by DKAudio on 2009-01-11
Please...see my above post as to what I did...

---

### Post by DKAudio on 2009-01-17
Up again, I thought this would be a simple fix.  I can't believe no one has enabled 3D graphics on a non-able video card before.

---

### Post by vulcanfk on 2009-01-17
Boot up the machine to a command line, log in, and paste the output of what cariboo907 suggested.

When you boot up to the command line, cd to your /etc/X11 directory.  If there's an xorg.conf backup file, mv xorg.conf to xorg.conf.nvidia and mv the backup to xorg.conf.

---

### Post by DKAudio on 2009-01-18
Thank you so much for replying!

Sorry but you lost me.  

I am very new to Ubuntu (2 weeks).

Normally when you boot I have an option to hit the esc key to get to a menu.  Is that where I want to go?

I did some reading and know what command line is (non graphical command prompt type).  I do not know that language or how to get there though.

If you could please tell me what to do set by step in laymens terms that would be awesome.

---

### Post by vulcanfk on 2009-01-18
Yep, hit esc.  You'll  want to select the recovery option, then boot to a root console.  When it prompts, login as whatever user you set up.  Once logged in, type:
```
cd /etc/X11
ls
```
That will give you a listing of files in the directory.  Whatever NVIDIA installer you used probably created an xorg.conf.bak file.  If it's there:
```
mv xorg.conf xorg.conf.nvidia
mv xorg.conf.bak xorg.conf
```
Then reboot normally.  That should fix your problem.

If its not there, do what cariboo907 suggested.
```
lspci | grep VGA
```
and paste the output here.

---

### Post by DKAudio on 2009-01-18
Thank you so much!

When I type 

cd /etc/X11
ls

and I see a xorg.conf.bak file what should I do with it, delete it?

What is the proper way to get out of the command line and do a reboot (does ctrl+alt+del work there to reboot?)

I am out all week on a business trip but I am going to try this first thing friday when I land.  Thanks again, I will reply with the result.

Dan

---

### Post by vulcanfk on 2009-01-19
If there is a file named xorg.conf.bak
```
mv xorg.conf xorg.conf.nvidia
```
moves (renames) xorg.conf to xorg.conf.nvidia.  This creates a backup of the xorg.conf file that nvidia configured.
```
mv xorg.conf.bak xorg.conf
```
then moves xorg.conf.bak (the backup file) to xorg.conf.

To reboot from the command line
```
sudo shutdown -r now
```

---

### Post by DKAudio on 2009-01-19
Perfect, thanks a million.  I will try this on Friday (if I make it home on time).

---

### Post by DKAudio on 2009-01-23
ok, I was able to do the following command...

mv xorg.conf xorg.conf.nvidia

But when typing...
mv xorg.conf.bak xorg.conf

It replied...
mv:cannot stat 'xorg.conf.bak': No such file or directory

I then typed lspci | grep VGA and it replied...

01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 420 Go] (rev a3)

---

### Post by DKAudio on 2009-01-23
Hmmm, it seems that moving the first file worked!  My video is back to normal.  Thank you so much, I really appreciate it and learned a little in the process.

Thanks again.

---

