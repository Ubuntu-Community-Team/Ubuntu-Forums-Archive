---
title: "Switched video driver - lost display"
date: 2011-05-13
forum: Mythbuntu
---

### Post by mookie60 on 2011-05-13
mythbuntu 10.04/.23
nvidia 8400gs


I was using the Nvidia driver ("current version") but had started getting some thin horizontal bars during playback of recordings, but only when there was motion in the video.   So I thought I'd try the linux video driver.   This had previously worked pretty well with 9.04.

After rebooting with the new driver, there is no longer any display.  I do see the image while it does it's POST, then it dies.  I also only see the POST if I use the video card's s-video output.  I get nothing with the VGA output.  I also pulled the video card and used the on-board VGA, but again no display at all.

So with the video card back in, I can at least see the POST via the s-video.  Even though I can't see it, the OS is booting, because I can view Mythweb on my browser.   I'm sure I can probably boot from a live CD, but don't see how this would help.   

How do I switch back to the Nvidia driver without seeing the screen?   Is there an option during boot where I might be able to force a low-res mode?

I've never used SSH, would it have been enabled by default?  

Any suggestions greatly appreciated, thanks.

---

### Post by Dan_R on 2011-05-13
SSH should be enabled by default unless you unchecked it during the installation of the OS. A good SSH program I use is PuTTY for Windows. You just need to know the IP address of the machine to connect, and your username and password to login.

Get it here [http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)

What I would do in this situation is download an older version of the driver version you know works. That can be done by using a command similar to below, using wget and pasting the download link in, in PuTTY paste is right click.

```
wget http://us.download.nvidia.com/XFree86/Linux-x86/173.14.28/NVIDIA-Linux-x86-173.14.28-pkg1.run
```

It will download it to your current SSH directory, and you can run it by doing

./sh   put in a space, type the first few letters of the file, ex 173 and hit TAB and it should fill out the file name, then hit enter and the installer should start. 

```
./sh 173.14.28/NVIDIA-Linux-x86-173.14.28-pkg1.run
```

If it complains about permissions, you may need to login as root, so do "sudo su" hit enter and type in your root password and try again. If it complains about gdm running, do the following 

```
service gdm stop
```

After the installation I would restart and see if your display returns. You can do that by running the command "shutdown -r now"

---

### Post by mookie60 on 2011-05-13
My username is Myth.  I'm using my laptop, (ubuntu 10.04).   I tried ssh and got this:

>   ssh myth@192.168.1.100
ssh: connect to host 192.168.1.100 port 22: Connection refused

It's entirely possible I may have disabled ssh.  Would that give me the "connection refused"?   It should have prompted me for a password, right?

Thanks

---

### Post by mookie60 on 2011-05-13
Just tried booting into recovery mode - same problem, display just goes blank.

Is there a way during the boot process to force it to boot to a command line?

---

### Post by mookie60 on 2011-05-14
Well it's fixed, sort of.

I had tried using just the on-board graphics (graphics card removed) connected via vga to a sony flatscreen tv (which I used to use over a year ago with 9.04), but it had the same problem.  This time I tried the same thing, except using an old crt monitor - it worked and I was able to switch back to the nvidia driver.  This monitor was actually next to the front door, awaiting a trip to the recycle center.   

So I'll mark it solved, though I'm back to square one figuring out the video quality problem.

---

