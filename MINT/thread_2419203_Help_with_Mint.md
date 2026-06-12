---
title: "Help with Mint?"
date: 2019-05-17
forum: MINT
---

### Post by daxusb on 2019-05-17
Hello. Pretty inexperienced with Linux here. My friend gave me a usb drive with a Mint installation on it because I was having issues with windows. Got it installed no problem. Mint seems pretty user friendly. Worked great for a week then last night I turned my laptop off without shutting down. Now when I boot it back up I get the options to boot mint normally, in recovery mode, or system settings. When I boot mint normally I get this from the computer and am left at a prompt. 

[0.004000] do_IRQ: 1.55 no irq handler for vector
[0.004000] do_IRQ: 2.55 no irq handler for vector
[0.004000] do_IRQ: 3.55 no irq handler for vector
[7.488264] Couldn't get size : 0x8000000000000000e

BusyBox v1.27.2 (Ubuntu 1:1.27.2-2ubuntu3.2) built-in shell (ash)
Enter 'help' for a list of built in commands.

(initramfs)


That's it. It leaves me at the prompt. I've typed help and gotten the list of commands but being newer to Linux they don't mean much to me. 

Booting into recovery mode doesn't help. Just gives more code (than I'm wanting to copy character for character), and ends with the same codes and leaves me at the prompt. 

Did I break it? Can I fix it? Can I just tell it to stop being broken and boot back into that wonderfully user friendly mint I was using before? (I formatted the usb drive with the mint installation on it already...it was working great!)

Anybody who is willing to help me, I'd appreciate it alot. Thanks.

---

### Post by oldfred on 2019-05-17
Moved to Mint sub-forum.

If you did an abnormal shutdown, you often have to run fsck for ext4 or if Windows chkdsk for NTFS partitions.
Whatever files were open or running may need repair.

To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by daxusb on 2019-05-17
I guess you missed the part where I said I was new?

sudo parted-| 
> (It returns nothing and leaves me at a prompt...again)

You're gonna have to talk to me like a baby I literally have no idea what any of the stuff you said means or which parts of it are commands? Not here to make myself feel dumb...trying to learn but nobody to teach me. If you could walk me through this that would be really great. :)

---

### Post by Rubi1200 on 2019-05-18
Let's take one step at a time.

At the BusyBox prompt type this:

```
parted -l
```

Note that is a lower case l not L and not 1

Post back here with the results please.

---

### Post by daxusb on 2019-05-18
Thank you Rubi1200!

(initramfs) parted -i
sh: parted: not found
(initramfs)

You probably know this but just to clarify the (initramfs) is the prompt it gives me.

---

### Post by Rubi1200 on 2019-05-18
When you get initramfs type exit then Enter and it should tell which partition has the problem.

Post that back here so we can try fixing it.

---

### Post by daxusb on 2019-05-18
Okay. It gave me about 20 lines of code. I tried to take a picture hoping I could post that here but I can't seem to figure that out. 

At the end this seems to stand out.

dev/sda2: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
(i.e., without -a or -p options)
fsck exited with status code 4
The root filesystem on /dev/sda2 requires a manual fsck.

Then it just gives me the BusyBox version and leaves me at the prompt again. 

If you would like a picture of the code, I could email it to you...I feel like there must be a way to post pictures on here...maybe I'm just trying too damn hard.

---

### Post by Rubi1200 on 2019-05-18
No need to email, we have enough information now.

The problem is on /dev/sda2

Here is what you need to do.

Get back to the BusyBox and again at initramfs type exit and then Enter.

The you need to type this at the prompt:

```
fsck -y /dev/sda2
```

There might be prompts during the process and in most cases it is fine to answer yes (y).

Once it is completed it should hopefully tell you all is fixed and then you can type reboot to start the system again.

---

### Post by daxusb on 2019-05-18
Okay well I did that and we definitely made some progress. 

Question...was I able to reboot while this process was active? Hopefully not. It asked me if something was okay, and when I typed y for yes...nothing happened. Pushed enter...nothing happened. Thought it was done...so I typed reboot and it turned off and rebooted. 

Get the mint loading screen this time...then a prompt for my PC login. I think it does that automatically though because that just showed up for a second...then went away and started shooting tons of error messages at me. It would give me like 5 then wait a couple minutes and another 5 would show up...and so on and so on until I realized it was 1:30 in the morning and my toddler is going to be waking me up in like 4 hours. 

So needless to say I gave up and shut her down again. I'm off to bed now. I'll come back tomorrow and try to copy some of those error codes for you if you're still around tomorrow. If not thanks for your help. You're probably shaking your head at me right now and calling me names under your breath. I fear I may have messed it up more. Gnight for now.

---

### Post by Rubi1200 on 2019-05-18
Progress is good.

Get some rest, tomorrow is another day.

No names under breath from me and no head shaking, no worries.

Stuff like this happens and usually it can be fixed so we will try again when you are ready.

---

### Post by yancek on 2019-05-18
> Okay. It gave me about 20 lines of code. I tried to take a picture hoping I could post that here but I can't seem to figure that out. 


When you are posting a reply there are 3 rows of icons above the message window and the one you want is the paper clip icon on the upper right.  Click that and a new window opens and click Add Files in the upper right of that window and browse to the location of the file and upload.

---

### Post by daxusb on 2019-05-18
Ah yes! I see that now when I click the "go advance" reply option. I was just doing quick replies before that. Thanks for your help!  I'll get some pictures of those errors after I turn it on again.

---

### Post by daxusb on 2019-05-18
Rubi1200!

I booted it up again and didn't get the same error codes as last night. It just started up at the busybox prompt. I did what you said again. I typed exit, and it told me sda2 again. I did what you said again and did the fsck -y dev/sda2, and this time I let the process finish! When it was complete, about 10 minutes. It said the file system has been modified. I told it to reboot and it did, it shot the first errors at me again, then flashed my PC login, and then it opened mint! I'm now at my desktop!

Thanks very much for your help! For the purpose of learning, could you explain exactly what we did there? For example what is fsck?

---

### Post by DuckHook on 2019-05-18
**F**ile
**S**ystem
**C**hec**K**

Essentially, what Rubi1200 asked you to do was to invoke the ***fsck*** utility to check and repair your broken filesystem in sda2. The ***-y*** flag tells *fsck* to go ahead with any repairs automatically without first checking back with the user interactively. The */dev/sda2* is the system reference for the second partition on your first SATA disk.

FWIW, oldfred said exactly the same thing, but in shorthand. Please appreciate that for us oldtimers, Linux has lost a lot of its initial obscurity and some of the more exotic commands have become natural. We forget what it's like for newbies.

If you wish to continue using Linux, it's a good idea to familiarize yourself with it more deeply. While many users get by with nothing more than superficial knowledge, once system problems rear their ugly heads, a slightly deeper understanding pays big dividends. A good place to start is the links in my sig: *Linux is Not Windows* & *Resources for Newcomers*.

---

### Post by oldos2er on 2019-05-18
> **daxusb said:**
>  what is fsck?

It's roughly equivalent to DOS/Win's chkdsk command, and fulfills the same function. ```
man fsck
``` for technical details, and feel free to ask if you have further questions.

Mint maintains their own support forum [here]("https://forums.linuxmint.com/") ; they are friendly and welcoming to new users.

---

### Post by Rubi1200 on 2019-05-18
> **daxusb said:**
> Rubi1200!

I booted it up again and didn't get the same error codes as last night. It just started up at the busybox prompt. I did what you said again. I typed exit, and it told me sda2 again. I did what you said again and did the fsck -y dev/sda2, and this time I let the process finish! When it was complete, about 10 minutes. It said the file system has been modified. I told it to reboot and it did, it shot the first errors at me again, then flashed my PC login, and then it opened mint! I'm now at my desktop!

Thanks very much for your help! For the purpose of learning, could you explain exactly what we did there? For example what is fsck?

I am also very happy to hear the problems have been resolved.

Enjoy!

---

