---
title: "[SOLVED] Wake-on-LAN: Frontend waking up the Backend?"
date: 2008-09-02
forum: Mythbuntu
---

### Post by Verzweifler on 2008-09-02
I do have my Mythbuntu MasterBackend sitting in the basement, whereas my FrontEnd is located upstairs (a typical setup, though). The BackEnd is not up 24/7; it wakes up for recordings as well as for predefined time slots (to save some energy).
My FrontEnd is a DisklessFrontEnd, so it boots its image over LAN from the BackEnd and, therefore, requires the BackEnd to be up in order to be able to boot properly.

At the moment, I have the following issue: Whenever I like to watch TV _outside_ the predefined time slots, I have to go down to the "serverroom" and switch on the BackEnd, then go up, wait for a moment and finally switch on the FrontEnd. Quite uncomfortable! However, I do not want to change my concept of saving energy, so modifying the slots is not an option.

So I came across the following idea:
What about booting the FrontEnd from a USB stick once it receives no PXEBoot-image (i.e. the BackEnd is down), then quickly sending the magic WOL packet to the BackEnd (it supports WOL, so no problems here) to wake it up, wait for some moments and then reboot, which will then be a PXE-boot because the BackEnd is up? 

But: I have no idea how to do this in a _smart_ way. Well, installing a more or less complete Linux on the USB for just sending a WOL to the server to me seems to be an overkill. Does anybody know about a small Linux image doing the job without all the fancy Linux startup, i.e. just uncompressing the kernel, sending the WOL package to a configurable MAC address, waiting for let's say 30 seconds and then rebooting?

---

### Post by laga on 2008-09-02
> **Verzweifler said:**
> 

So I came across the following idea:
What about booting the FrontEnd from a USB stick once it receives no PXEBoot-image (i.e. the BackEnd is down), then quickly sending the magic WOL packet to the BackEnd (it supports WOL, so no problems here) to wake it up, wait for some moments and then reboot, which will then be a PXE-boot because the BackEnd is up? 

But: I have no idea how to do this in a _smart_ way.

That's already possible if you use Mythbuntu-diskless.

Step 1) Start mythbuntu-control-centre
Step 2) Go to the diskless tab
Step 3) Look in the "Client bootable flash drive" section
Step 4) Choose your USB thumb drive
Step 5) Check the "Wake on LAN" checkbox and enter the MAC address of your backend
Step 6) Click "Write Drive"
Step 7) Boot your frontend from that pen drive
Step 8) Let me know if it works because. I don't think I've ever tested that properly ;)

---

### Post by Verzweifler on 2008-09-02
Hi laga,

it's time for another thank you... 
After following the steps proposed, I ended up with a bootable USB stick. Since my BackEnd is currently up and running, I did a test run with my eyes close to the output out the bootup sequence. I verified that there was sent a WOL package (I saw a "waking up" and the MAC address I entered before flying by) and due to the fact that the server was up, my FrontEnd was able to load its image without having to wait... 

I'll try booting later today with the BackEnd down (not feasible right now because of some recordings) and will report the outcome. 

However, I am really surprised that it was THAT easy...

---

### Post by volkswagner on 2008-09-02
Uh, um, I gotta get a diskless up and running.  My fingers are crossed for you Verzweifler.

:popcorn: for you laga!

---

### Post by Verzweifler on 2008-09-03
Wow, that is a really cool thing...

To cut it short: IT WORKED!

The only thing that is a drawback on the Woman-Acceptance-Factor is the missing splash screen. Watching text messages scrolling by is no good for wife and kids impatiently waiting for the box to just show the familiar mythtv menue.
Even worse, some of the messages are irritating especially those errors printed while the FrontEnd is trying but not able to connect to BackEnd still in progress of booting.
Is there a simple way to add a splash?

---

### Post by anonymousdog on 2008-09-03
With easy diskless server setup, sub-$100 frontends become feasible; the largest expense often being a remote/ir receiver.  The standard diskless server setup also gives you about 80% of the setup required for a MediaMVP/mvpmc frontend which is just fine for viewing and scheduling recordings (though I've had problems with channel change in LiveTV) and includes a remote.  Those suckers can be had new for about $90 with shipping.

---

### Post by Verzweifler on 2008-09-06
I finally found the solution to the remaining issue of a non-existent bootsplash:

I simply added "splash" to the append command found in the syslinux.cfg on the USB-stick.

That did the trick and I am now perfectly satisfied...

---

### Post by laga on 2008-09-06
> **Verzweifler said:**
> I finally found the solution to the remaining issue of a non-existent bootsplash:

I simply added "splash" to the append command found in the syslinux.cfg on the USB-stick.

That did the trick and I am now perfectly satisfied...



I wonder why that didn't work out of the box.

Can you file a bug report so I don't forget to look into it?

I wonder what happens if the server needs to do a file system check. I haven't timed how long that takes on my MythTV backend.

---

### Post by Verzweifler on 2008-09-07
> **laga said:**
> I wonder why that didn't work out of the box.

I also was surprised about that... I just could not believe my eyes when after adding the "splash" all worked as expected. It was THAT easy...?!

> **laga said:**
> Can you file a bug report so I don't forget to look into it?
Will do, laga...

> **laga said:**
> I wonder what happens if the server needs to do a file system check. I haven't timed how long that takes on my MythTV backend.
That should not be a big deal. The script just waits for nbd becoming available, so it will take some more time. A file system check on my machine will approx. take another 2-3 min, but I already handled that issue by checking for upcoming checks during one of my shutdown scripts. Since my BackEnd is scheduled to wake up every night at 4:00am to get EPG-info, all file system checks are delayed to such event, i.e. when my script determines that the next planned wakeup of the machine is NOT scheduled for grabbing EPG it just substracts 1 from the countnumber (using tune2fs) to make sure there is no check when waking up for a recording...

---

### Post by laga on 2008-09-07
> **Verzweifler said:**
> 
That should not be a big deal. The script just waits for nbd becoming available, so it will take some more time.


Yeah, but there is a time out - a few minutes, if I recall correctly.

> 
 A file system check on my machine will approx. take another 2-3 min, but I already handled that issue by checking for upcoming checks during one of my shutdown scripts. Since my BackEnd is scheduled to wake up every night at 4:00am to get EPG-info, all file system checks are delayed to such event, i.e. when my script determines that the next planned wakeup of the machine is NOT scheduled for grabbing EPG it just substracts 1 from the countnumber (using tune2fs) to make sure there is no check when waking up for a recording...

That's great. Did you post these scripts somewhere? I think I could use them ;)

---

### Post by Verzweifler on 2008-09-08
> **laga said:**
> 
That's great. Did you post these scripts somewhere? I think I could use them ;)
Your wish is my command, laga, although that is going off-topic...:-\"

You'll see attached two scripts (named sleep and fsck_check) and the file containing my scheduled uptimes. I hope the contents of the scripts are pretty much self-contained and understandable. (I modified them a bit, because they contained some sensitive data I did not want to publish on the Internet)

sleep is called by the MasterBackEnd when it decided to go to sleep and no other conditions prevented it. It goes through the uptimes file to determine whether the next scheduled wakeup will be due to a recording (a given as a parameter by MBE) or whether EPG grabbing or scheduled uptime will be the reason for the next wakeup. The result of this check is written to a file named "cause" and kept in variable $Cause...

Later on, sleep checks the cause for the next wakeup. If $Cause == "EPG" then nothing happens, otherwise fsck_check is called to check whether the next wakeup will cause a fsck... If so, the script just modifies the mountcounts in order to prevent such check. Remember that in case of the next EPG grabbing, such "delayed" check is then performed (with no harm to recordings)

---

### Post by kuilboer on 2011-01-09
I was very pleased to find this post because this is exactly what I am trying to accomplish. 

As of this moment I have setup the Mythbuntu backend, Installed the Diskless-Server Package. Configured the diskless client image and am able to PXE boot into it. 

I used the [ACPI Wakeup documentation from the Mythtv Wiki]("http://www.mythtv.org/wiki/ACPI_Wakeup") to configure controlled backend shutdown and automated wakeup.

The backend server is configured to respond to WOL Magic packages. I tested this using the wakeonlan perl script and it also works.

The last step in this journey is getting the diskless front end to wakeup the Backend when required before trying to boot in to PXE. 

However Ubuntu has discontinued the diskless tab after 9.04. And while all the functionality should still be there, according to Ubuntu, I have been unable to find the documentation for it. 

So if anyone knows where to find this docmentation please let me know.

regards,

Olaf Kuilboer

---

