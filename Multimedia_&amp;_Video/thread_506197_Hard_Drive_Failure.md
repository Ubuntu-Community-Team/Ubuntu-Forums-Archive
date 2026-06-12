---
title: "Hard Drive Failure?"
date: 2007-07-21
forum: Multimedia &amp; Video
---

### Post by maclenin on 2007-07-21
I will try to be as concise as possible re: a troubling sequence of events.

A. Background:

Dell Inspiron 600M.
Ubuntu 6.10.
My laptop is always running.
I run a screen saver that shuts off after about an hour or so of in activity. 
The cooling fan sounds like it has been acting up, over the past 3 weeks....

B. The Troubling Sequence of Events:

1. I woke up this morning and logged into my computer (unaware of what lay ahead).

2. When I tried to check my email, the email program would not load (i.e. the hard disk didn't seem to spin).

3. I opened windows of already-open programs - these windows opened slowly - but did, eventually, display data.

4. I opened the terminal and attempted a restart:

```
sudo shutdown -r +0
```

5. I immediately received an error akin to (I am not certain that this is the exact error message - but after doing a little research, I think this is close to what I received)...

```
bash: /sbin/shutdown: Input/output error
```

6. I hard shutdown the laptop using the power button.

7. I powered up the laptop with the power button and it went through its early boot sequence and GRUB to the "Start" sequence - i.e. with the ubuntu logo - where the process froze. The hard drive light was on - but the computer would not load any further.

8. I shut down the computer, again, with the power button.

Options I've Begun to Explore:

9. I powered up, again, booting from the liveCD.

10. I was able to run a...

```
sudo fdisk -l
```

...command and saw the partitions on my "faulty" hard drive - as I had set them up - with no apparent error messages.

Next Steps?

I am going to try - after I let the laptop cool a bit - to mount the partitions via liveCD and recover whatever data I am able to recover....

Any other suggestions - troubleshooting tips?

I was just about to back-up my drive....

Thanks for whatever information you folks might be able to pass along.

---

### Post by tgalati4 on 2007-07-21
You could have had a runaway process that kept your machine at 100% CPU and caused an overtemp condition.  Leave the machine off for several hours and then boot and note its behavior.

You can load SMART monitoring tools to read the error conditions and temperature on the disk drive.


>sudo apt-get install smartmontools

Search the forums for tutorials on how to set it up.  It will give you some more info as to what is going on.

---

### Post by maclenin on 2007-07-22
Thanks for the mere suggestion that it wasn't a hard drive explosion....

In the interim, after letting the laptop cool for a few hours, I re-started and received, in summary, the following error message:

```
fsck died with exit status 8
```

After a little more research I was directed to this howto (thanks, ingo):

[B][U][http://ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub](http://ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub)
[/U][/B]

I am planing to give it a whirl, however, the status 8 error, according to the GRUB manual...

[B][U][http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html#Stage2-errors](http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html#Stage2-errors)
[/U][/B]

...means:

```
8 : Kernel must be loaded before booting

This error is returned if GRUB is told to execute the boot sequence
without having a kernel to start. 

```

Any thoughts about whether restoring GRUB is, indeed, the answer or whether I need to address the kernel, somehow....

I'll report back as I am able to attack this issue.

In the meantime, I have been able to retrieve files from my hard drive via liveCD....

Thanks for the reply.

---

### Post by maclenin on 2007-07-27
I think I have come to slightly better understanding of what's happening:

1. fan failure
1.a. overheating 
2. hard drive death throes (maybe related to 1. + 1.a.)
3. 1. + 1.a. + 2. leading to hard drive lock-up....

It's time to get a new machine.

Do the symptoms match the possible diagnosis?

---

