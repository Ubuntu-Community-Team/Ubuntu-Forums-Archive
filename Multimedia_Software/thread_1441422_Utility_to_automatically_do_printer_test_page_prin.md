---
title: "Utility to automatically do printer test page print job?"
date: 2010-03-28
forum: Multimedia Software
---

### Post by Rocket J Squirrel on 2010-03-28
I have a couple of large-format printers (Epson R2400, HP 9650) which I only use infrequently. If they are not used very often, they dry out, the print heads get packed up, it's an expensive mess to deal with when times comes to run off some prints. 

The printers are physically connected to a Windows machine to which my Ubuntu computer is networked. 

It would be helpful if there was a utility that could initiate a test page print job on the machines, which could be scheduled to run once a week or so. I've had no luck finding such a thing for Windows. 

Is there such a thing for Linux?

---

### Post by sybille on 2010-03-28
You could set this up yourself, using the cron utility to print the Ubuntu printer test page from the command line at whatever interval you'd like.

To print a test page from the command line, you need to find the names of each of the printers. You should be able to find the names by looking at the web interface to CUPS, the printing system:
[http://localhost:631/printers/](http://localhost:631/printers/)
Look for "Queue Name."

Once you know the names, you can print a test page using the command line (i.e. Terminal, located in Applications -> Accessories -> Terminal) as follows:
```
lpr -P <name of printer> /usr/share/system-config-printer/testpage-letter.ps
```Replace <name of printer> (including the brackets) with the name of one of your printers. Try for each printer that you want to test-print on schedule. 

So, if all of the above goes well, you can set up the scheduling interval, using cron. Cron should be running on your system already. Here's more information about what it is:
[http://en.wikipedia.org/wiki/Cron](http://en.wikipedia.org/wiki/Cron)
That wikipedia entry explains how to use cron. Essentially, you edit a file, called the crontab, and tell it what command to run and when to run it. Here are some more how-tos that might be helpful as well:
[http://ubuntuforums.org/showthread.php?t=102626](http://ubuntuforums.org/showthread.php?t=102626)
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)
Another option is to use the graphical cron configuration tool called "gnome-schedule", but I've never used that myself.

If you've never done this kind of thing before, the procedure I just described might seem complex or difficult. But it's not, really, and it is worthwhile to learn a little about cron since it can really come in handy for all sort of repetitive things.

---

### Post by Rocket J Squirrel on 2010-03-29
Thank you, Sybille,

lpr is not happy with the way I am formatting the path to the printer. 

[http://localhost:631/printers/](http://localhost:631/printers/) shows one of the printers as

smb://CCIRCLE/FUJITSU-LAP/Mikes%20Office

When I do the command line as 

```
lpr -P <smb://CCIRCLE/FUJITSU-LAP/Mikes%20Office> /usr/share/system-config-printer/testpage-letter.ps
```I'm getting "bash: smb://CCIRCLE/FUJITSU-LAP/Mikes%20Office: No such file or directory"

How should I format the printer path?

---

### Post by sybille on 2010-03-29
For lpr, The -P option asks for the *name* of the printer, not the *path* of the printer.

Let's see if the smbspool tool will print a test page for you. Try the following:
```
smbspool smb://CCIRCLE/FUJITSU-LAP/Mikes%20Office test 1 /usr/share/system-config-printer/testpage-letter.ps 
```Please post whatever output that command gives you.

If that doesn't work, there are other ways to look for the printer name.

---

### Post by Rocket J Squirrel on 2010-03-29
Hi Sybille,

Okay, that returned:

```
jackelliott@ubuntu:~$ smbspool smb://CCIRCLE/FUJITSU-LAP/Mikes%20Office test 1 /usr/share/system-config-printer/testpage-letter.ps
Usage: smb://CCIRCLE/FUJITSU-LAP/Mikes%20Office [DEVICE_URI] job-id user title copies options [file]
       The DEVICE_URI environment variable can also contain the
       destination printer:

           smb://[username:password@][workgroup/]server[:port]/printer
jackelliott@ubuntu:~$ 
```Followed by a CUPS server error: server-error-server-not-available

Thank you for looking into this.

---

### Post by sybille on 2010-03-29
Well, I'm going to start being not too much help, I fear, simply because I don't have any printers networked over Samba to verify the commands I'm suggesting. 

Although the smbspool error you posted looks to me like it's more of a syntax problem than anything else, I'd like to try a different approach first.

Could you try the following command?
```
lpstat -p
```Please post the output.

BTW, If you want to learn more about any of these commands and their options, you can run "man" plus the command in a terminal (i.e. **man lpstat**). This will display the manual page for the command. Press "q" to exit a man page.

---

### Post by Rocket J Squirrel on 2010-03-29
LOL, well we all run up against our knowledge limits at one point or the other. You know more about CLI stuff than I, and I appreciate you having a go at it. 

Here's the output of lpstat -p

```
jackelliott@ubuntu:~$ lpstat -p
printer Epson-Stylus-Photo-R2400 is idle.  enabled since Sun 28 Mar 2010 03:27:27 PM PDT
printer HP-Deskjet-9600 is idle.  enabled since Sat 27 Mar 2010 11:31:06 PM PDT
printer HP-Officejet-Pro-8500-A909g is idle.  enabled since Sat 27 Mar 2010 09:41:38 PM PDT
printer HP_Shop_Printer is idle.  enabled since Sat 27 Mar 2010 10:28:24 PM PDT
printer MikeDesktop is idle.  enabled since Sat 27 Mar 2010 09:37:41 PM PDT
```

---

### Post by sybille on 2010-03-29
OK, that's perfect.

All the items on the list there after "printer" are the names of the various printers your system knows. So, those are the names to use, one at a time, in the lpr command I posted earlier.

So, can you try printing a test page with lpr again, to each of the relevant printers?

---

### Post by Rocket J Squirrel on 2010-03-29
Thanks, Sybille

Tried it a couple ways:
```

jackelliott@ubuntu:~$ lpr -P <MikeDesktop> /usr/share/system-config-printer/testpage-letter.ps
bash: MikeDesktop: No such file or directory

jackelliott@ubuntu:~$ lpr -P MikeDesktop /usr/share/system-config-printer/testpage-letter.ps
```The second way did not return an error in Terminal, but no test page printed and a print spool window opened showing the job as "stopped" and with a dialog box saying that "There was a problem processing document 'testpage-letter.ps'

testpage-letter.ps does exist in the expected folder.

---

### Post by sybille on 2010-03-29
You don't need the brackets; the second way you used is the correct one.

So, on with the troubleshooting for printing from the command line.

A question: can you sucessfully print a test page to the printer named "MikeDesktop" using the GUI tool? I.e., open System -> Administration -> Printing, Right click on the "MikeDesktop" icon, choose Properties, and then choose the "Print Test Page" button. Does that work?

Also, could you try this:
```
lp -d MikeDesktop /usr/share/system-config-printer/testpage-letter.ps
```

---

### Post by Rocket J Squirrel on 2010-03-29
Interesting. On Saturday, when I installed the printer, the test page printed. Now I am getting the same error as lpr got: "there was a problem processing document `test page' (Job 8)"

From the Windows machine to which it is connected, it works.

---

### Post by sybille on 2010-03-29
Well, that's a problem. Can you print anything to that printer?

You could try turning on verbose logging for CUPS to see whether there are any potentially interesting error messages. You can find out how to that in the Ubuntu wiki, at the following link:
[https://wiki.ubuntu.com/DebuggingPrintingProblems#CUPS%20error_log](https://wiki.ubuntu.com/DebuggingPrintingProblems#CUPS%20error_log)

---

### Post by Rocket J Squirrel on 2010-03-29
More interesting. Of the five printers: 

```
jackelliott@ubuntu:~$ lpstat -p
printer Epson-Stylus-Photo-R2400 is idle.  enabled since Sun 28 Mar 2010 03:27:27 PM PDT
printer HP-Deskjet-9600 is idle.  enabled since Sat 27 Mar 2010 11:31:06 PM PDT
printer HP-Officejet-Pro-8500-A909g is idle.  enabled since Sat 27 Mar 2010 09:41:38 PM PDT
printer HP_Shop_Printer is idle.  enabled since Sat 27 Mar 2010 10:28:24 PM PDT
printer MikeDesktop is idle.  enabled since Sat 27 Mar 2010 09:37:41 PM PDT
```
One is connected to one Windows machine, the other four on a second machine. 

The one printer that has been giving the error is the only one connected to that machine. As mentioned, it prints fine from that machine).

I just sent a test page to one of the four printers connected to the other machine and it prints fine. 

Also as mentioned, when I initially connected to the one machine and printer that are giving the error, it printed the test page, too. 

So there's something fishy going on with the one machine with the one printer. I think I'll delete that printer and have Ubuntu re-install it. I'll report back.

---

### Post by Rocket J Squirrel on 2010-03-29
Nope, no good. Darn.

---

### Post by Rocket J Squirrel on 2010-03-29
> **sybille said:**
> Well, that's a problem. Can you print anything to that printer?

You could try turning on verbose logging for CUPS to see whether there are any potentially interesting error messages. You can find out how to that in the Ubuntu wiki, at the following link:
[https://wiki.ubuntu.com/DebuggingPrintingProblems#CUPS%20error_log](https://wiki.ubuntu.com/DebuggingPrintingProblems#CUPS%20error_log)

No, nothing goes to that printer from here. I've switched CUPS to verbose and see if anything interesting turns up. This is a less-important printer than the ones that I started the thread with, so it's no big deal, the ones that need weekly prodding are working fine. 

Printing Troubleshooter for this printer says that the Server is not Exporting Shared Printers to the network, even though the Windows printer is marked as shared. This is another subject and something I'll bang on for a while myself. 

Many thanks for the help, Sybille. I'll tinker with cron and learn how to schedule weeks test page printing from the other printers. It looks I have the tools I need now.

---

### Post by sybille on 2010-03-30
> **Rocket J Squirrel said:**
> Printing Troubleshooter for this printer says that the Server is not Exporting Shared Printers to the network, even though the Windows printer is marked as shared. This is another subject and something I'll bang on for a while myself. 
In Ubuntu's Printer configuration dialog, when you right-click this printer, does is show that sharing is enabled? That's something to check, if you haven't already.

Otherwise, good luck with setting up cron. Hope it's not too much of a hassle to get it working. :)

---

