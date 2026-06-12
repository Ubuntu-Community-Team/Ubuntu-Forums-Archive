---
title: "Video Programs Crash - with either Oracle or OpenJDK JAVA"
date: 2015-06-23
forum: Multimedia Software
---

### Post by Rick St. George on 2015-06-23
Running Latest LTS UbuntuStudio with AMD 8 core CPU, 16 GB Ram, 500 GB SSD.

After installing JAVA from Sun, my Video processing software crashes. No matter which version of JAVA I select (Oracle or OpenJDK Java 7) the programs still Crash! Blender; Brasero; DVD Styler; Kdenlive; Pitivi.

Any suggestions will be very much appreciated. This is why I built this system and chose UbuntuStudio. I have the two version of JAVA due to a Trading Platform from my Broker so I can watch the Market and place Trades in Real Time. The platform runs via Oracle Java.

Thanks,
Rick

---

### Post by Rick St. George on 2015-06-25
No Reply ... maybe this should be moved to another segment. Is there a Moderator reading this ? ? ?

Just saying ! ! !

---

### Post by monkeybrain20122 on 2015-06-25
It is hard to help without any error message. A stab in the dark would be that you may need to upgrade to java8,

---

### Post by QIII on 2015-06-25
Hello!

The members of the Forum Staff, volunteers all, are not all-knowing.  There are fewer than 30 of us, about 10 of whom are logged in at any moment and not all are at their keyboards every moment they are.  We cannot possibly read every post.  We can't dictate that every post be answered.

To echo the comment above, the lack of information as error messages leaves us all with little chance of spontaneously divining the issue.

It would be very helpful if you could start an application from the terminal and, when it crashes, copy the messages and post them here.

Information is always helpful.

---

### Post by Rick St. George on 2015-06-26
> **monkeybrain20122 said:**
> It is hard to help without any error message. A stab in the dark would be that you may need to upgrade to java8,

There is no Error Message. 

I am assuming that Java would update itself. I have Oracle Java 8 and Open JDK 7 installed.

All programs listed just crash and dissappear when I go to compile (or render) the video prior to burning.

Stumped ! ! !

---

### Post by Rick St. George on 2015-06-26
> **QIII said:**
> Hello!

The members of the Forum Staff, volunteers all, are not all-knowing. (SNIP) ... Information is always helpful.

Surely you must realize that we understand we are not posting to God. 

I simply posed a question that maybe I'm in the wrong category!

See recent posting for more of the only helpful info I can provide.

Peace,
Rick

---

### Post by monkeybrain20122 on 2015-06-26
> **Rick St. George said:**
> There is no Error Message. 

I am assuming that Java would update itself. I have Oracle Java 8 and Open JDK 7 installed.

All programs listed just crash and dissappear when I go to compile (or render) the video prior to burning.

Stumped ! ! !

If you have both openjdk and oracle java then you need to pick one to use. The default is openjdk7 so if your application requires java8 or Oracle java then it won't run. 
[http://askubuntu.com/questions/159575/how-do-i-make-java-default-to-a-manually-installed-jre-jdk](http://askubuntu.com/questions/159575/how-do-i-make-java-default-to-a-manually-installed-jre-jdk)

---

### Post by Rick St. George on 2015-06-26
> **monkeybrain20122 said:**
> If you have both openjdk and oracle java then you need to pick one to use. The default is openjdk7 so if your application requires java8 or Oracle java then it won't run. 


As mentioned in #1 above, 
> 
No matter which version of JAVA I select (Oracle or OpenJDK Java 7) the programs still Crash!
 

I select via the command prompt in terminal. (see Post #10 at)
[http://ubuntuforums.org/showthread.php?t=2273465](http://ubuntuforums.org/showthread.php?t=2273465)

Rick

---

### Post by monkeybrain20122 on 2015-06-26
I don't think kdenlive, DVD styler and brasero are java programs. So maybe it is something else. What happen if you launch any of these in the terminal? error message?

---

### Post by Rick St. George on 2015-06-26
Don't know how to launch in Terminal ???

---

### Post by monkeybrain20122 on 2015-06-27
Just type the program's name in the terminal (the program's name is a command to launch the programs) e.g to start kdenlive in the terminal, open the terminal, type
```
kdenlive
```
and press return.

---

### Post by Rick St. George on 2015-06-28
Tried "Brasero" in Terminal. Program opens/runs. But still program crashes/closes abruptily during attempt to render video.
These are MP4 files downloaded off YouTube.

Still Stumped ! ! ! 
Rick

---

### Post by monkeybrain20122 on 2015-06-28
> **Rick St. George said:**
> Tried "Brasero" in Terminal. Program opens/runs. But still program crashes/closes abruptily during attempt to render video.
These are MP4 files downloaded off YouTube.

Still Stumped ! ! ! 
Rick
 
What were the outputs on the terminal?

---

### Post by Rick St. George on 2015-06-29
> **monkeybrain20122 said:**
> What were the outputs on the terminal?

No Outputs in Teminal, it just ran the program.

---

### Post by Rick St. George on 2015-06-29
Finally get an Error:

Error while burning - SCSI error on write(0,16): See MMC specs: Sense Key B "Command aborted", ASC 00 ASCQ00

Here is the Partial (end)  Log file;

> 
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI error condition on command 2Ah WRITE(10): See MMC specs: Sense Key B "Command aborted", ASC 00 ASCQ 00.
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn Libburn reported an error SCSI error on write(115824,16): See MMC specs: Sense Key B "Command aborted", ASC 00 ASCQ 00.
BraseroLibburn called brasero_job_error
BraseroLibburn finished with an error
BraseroLibburn asked to stop because of an error
    error        = 1
    message    = "SCSI error on write(115824,16): See MMC specs: Sense Key B "Command aborted", ASC 00 ASCQ 00."
BraseroLibisofs stopping
BraseroLibisofs Getting out thread
BraseroLibisofs disconnecting BraseroLibisofs from BraseroLibburn
BraseroLibburn stopping
BraseroLibburn closing connection for BraseroLibburn
Session error : SCSI error on write(115824,16): See MMC specs: Sense Key B "Command aborted", ASC 00 ASCQ 00. (brasero_burn_record brasero-burn.c:2856)



This happened while trying to Burn pictures to a DVD disc.

Any suggestions?  What does this mean?

When attempting to Burn videos, during the Rendering phase, programs just crash. They don't even get to the burning phase.

Still stumped ! ! ! 

Rick

---

### Post by monkeybrain20122 on 2015-06-29
Google turns up this thread [http://askubuntu.com/questions/383481/burning-cds-with-brasero-error](http://askubuntu.com/questions/383481/burning-cds-with-brasero-error) But since you have problem with other applications you may have other issues.
BTW, do all your crashes involve dvds? Maybe dvd or drive is damaged?

---

### Post by Rick St. George on 2015-06-30
> **monkeybrain20122 said:**
> 
BTW, do all your crashes involve dvds? Maybe dvd or drive is damaged?


DVDs Yes, but it never gets to burn, crashed during rendering phase.
Everything in the computer is new. The drive is - LG 24x Super Multi Writer (model GS24NSBO).

Sorry ... didn't know this was to be a long thread ! ! !

Thanks for any help.
Rick

---

### Post by Rick St. George on 2015-07-01
Finally, after running DVDStyler and it CRASHES upon Rendering, I get an Error Window.

"SORRY, Ubuntu 14.04 has experienced an internal error. "

And in that window are a number of Items (can't copy and paste), and under "UnreportableReason", it shows;

"You have some obsolete package versions installed - ghostscript, libgs9, libgs9-common,
 Please upgrade these packages and check if the problem still occurs"

Checked to send this Error Msg. to help fix this problem.

Upgraded the above Pkgs.

DVDSyler Immediately CRASHED when attempting to Render video files.

Still Stumped ! ! !

---

### Post by Rick St. George on 2015-07-13
> **Rick St. George said:**
> DVDs Yes, but it never gets to burn, crashed during rendering phase.
Everything in the computer is new. The drive is - LG 24x Super Multi Writer (model GS24NSBO).
Thanks for any help.
Rick

CORRECTION: it is model GH24NSBO

---

### Post by Rick St. George on 2015-07-24
Noticed in CRASH / ERROR Pop-up for DVDStyler; 

"UnreportableReason: This is not an official Ubuntu package. Please remove any third party package and try again."

Can someone tell me where to post this Thread? Maybe this is not the correct forum!?! However, this happens with every DVD burner software as previously mentioned. Ubuntu Problem? Or is every CD/DVD burner package programmed to Crash?

Any suggestions appreciated.
Thanks,
Rick

---

### Post by QIII on 2015-07-24
The third line of your error log indicates that either the drive is balking because of the medium or Ubuntu is balking because of the drive.

Is the drive +R or -R?  Are the DVDs +R or -R?  Are they R or RW?  In most cases, +R devices will still write to -R and vice versa, but that is not always the case.  Brasero may have problems regardless of the device.

I use Kubuntu and so I use K3b.  I don't have any problems writing across formats.

Anyway, the question is, in short:  Are you using the correct media for your device?

I don't think Java should have anything to do with it, but since you noticed the issue after installing it, have you tried uninstalling both Oracle Java and Open JDK?

---

### Post by Rick St. George on 2015-07-24
Thanks for the Reply QIII.
No I haven't tried uninstalling Java. I need it on a daily basis to Trade via my Broker supplied Platform which uses Java.

As for the device, as previously mentioned, is a LG 24X Super Multi DVD Writer Model GH24NSBO, and Reads / Writes to DVD -/+ R or R/W media. My DVDs are -R Verbatim.  Just used Brasero to Copy a DVD. No problem. The problem seems only to be when a program such as DVDStyler, KdenLive, or K3B goes to RENDER a compilation. As soon as it starts the rendering phase ... they crash!

Too bad, too sad - I was loving UbuntuStudio ! ! !

Still stumped!?!  Any suggestions?

Rick

---

### Post by Rick St. George on 2015-11-15
I'm still trying to solve this problem.  I use KdenLive and K3b on my Laptop with no problem, but it is much slower than my Desktop. 

Any suggestions?

---

