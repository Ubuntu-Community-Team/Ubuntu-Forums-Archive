---
title: "Loosing internet connection"
date: 2010-02-05
forum: Networking &amp; Wireless
---

### Post by jwauton on 2010-02-05
[FONT=Arial][SIZE=2]I am runnning a PC with Ubuntu (Server)and have recently started having connection problems. The system is set up as per the FAQ at [http://www.neotel.co.za/support/pages/linux.aspx](http://www.neotel.co.za/support/pages/linux.aspx) (also posted in this forum)[/SIZE][/FONT]
 
[FONT=Arial][SIZE=2]When this happens the only way I have found to reconnect is to reboot the Ubuntu PC. Running poff Neotel followed by pon Neotel does nothing.[/SIZE][/FONT]
 
[FONT=Arial][SIZE=2]However, looking at the system log it is beginning to look like it is a problem with the USB device.[/SIZE][/FONT]
 
[FONT=Arial][SIZE=2]Log before reboot[/SIZE][/FONT]
 
[FONT=Arial][SIZE=2]Feb 5 19:06:59 ubuntu chat[3911]: alarm[/SIZE][/FONT]
[SIZE=2][FONT=Arial]Feb 5 19:06:59 ubuntu chat[3911]: Failed[/FONT][/SIZE]
[SIZE=2][FONT=Arial]Feb 5 19:07:31 ubuntu chat[3920]: abort on (BUSY)[/FONT][/SIZE]
[SIZE=2][FONT=Arial]Feb 5 19:07:31 ubuntu chat[3920]: abort on (NO CARRIER)[/FONT][/SIZE]
[SIZE=2][FONT=Arial]Feb 5 19:07:31 ubuntu chat[3920]: abort on (VOICE)[/FONT][/SIZE]
[SIZE=2][FONT=Arial]Feb 5 19:07:31 ubuntu chat[3920]: abort on (NO DIALTONE)[/FONT][/SIZE]
[SIZE=2][FONT=Arial]Feb 5 19:07:31 ubuntu chat[3920]: abort on (NO DIAL TONE)[/FONT][/SIZE]
[SIZE=2][FONT=Arial]Feb 5 19:07:31 ubuntu chat[3920]: abort on (NO ANSWER)[/FONT][/SIZE]
[SIZE=2][FONT=Arial]Feb 5 19:07:31 ubuntu chat[3920]: abort on (DELAYED)[/FONT][/SIZE]
[SIZE=2][FONT=Arial]Feb 5 19:07:31 ubuntu chat[3920]: send (ATZ^M)[/FONT][/SIZE]
[SIZE=2][FONT=Arial]Feb 5 19:07:31 ubuntu chat[3920]: expect (OK)[/FONT][/SIZE]
[SIZE=2][FONT=Arial]Feb 5 19:07:35 ubuntu chat[3920]: ~^?}#@!}!} } }9}!}$}%\}"}&} } } } }#}%B#}%}%}&EUe@ZC~~^?}#@!}!}!} }9}!}$}%\}"}&} }[/FONT][/SIZE]
 
[FONT=Arial][SIZE=2]Log after reboot[/SIZE][/FONT]
 
[FONT=Arial][SIZE=2]Feb 5 19:08:16 ubuntu chat[2505]: abort on (BUSY)[/SIZE][/FONT]
[SIZE=2][FONT=Arial]Feb 5 19:08:16 ubuntu chat[2505]: abort on (NO CARRIER)[/FONT][/SIZE]
[SIZE=2][FONT=Arial]Feb 5 19:08:16 ubuntu chat[2505]: abort on (VOICE)[/FONT][/SIZE]
[SIZE=2][FONT=Arial]Feb 5 19:08:16 ubuntu chat[2505]: abort on (NO DIALTONE)[/FONT][/SIZE]
[SIZE=2][FONT=Arial]Feb 5 19:08:16 ubuntu chat[2505]: abort on (NO DIAL TONE)[/FONT][/SIZE]
[SIZE=2][FONT=Arial]Feb 5 19:08:16 ubuntu chat[2505]: abort on (NO ANSWER)[/FONT][/SIZE]
[SIZE=2][FONT=Arial]Feb 5 19:08:16 ubuntu chat[2505]: abort on (DELAYED)[/FONT][/SIZE]
[SIZE=2][FONT=Arial]Feb 5 19:08:16 ubuntu chat[2505]: send (ATZ^M)[/FONT][/SIZE]
[SIZE=2][FONT=Arial]Feb 5 19:08:16 ubuntu chat[2505]: expect (OK)[/FONT][/SIZE]
[SIZE=2][FONT=Arial]Feb 5 19:08:16 ubuntu chat[2505]: ATZ^M^M[/FONT][/SIZE]
[SIZE=2][FONT=Arial]Feb 5 19:08:16 ubuntu chat[2505]: OK[/FONT][/SIZE]
[SIZE=2][FONT=Arial]Feb 5 19:08:16 ubuntu chat[2505]: -- got it[/FONT][/SIZE]
[SIZE=2][FONT=Arial]Feb 5 19:08:16 ubuntu chat[2505]: send (ATDT#777^M)[/FONT][/SIZE]
[FONT=Arial][SIZE=2]root@ubuntu[/SIZE][/FONT][FONT=Arial][SIZE=2]:~#[/SIZE][/FONT]
 
 
[FONT=Arial][SIZE=2]It looks like the modem is returning garbage in response to the ATZ^M command.[/SIZE][/FONT]
 
[FONT=Arial][SIZE=2]Any advice please?[/SIZE][/FONT]

---

### Post by puppywhacker on 2010-02-05
I'm impressed by your under 40 seconds reboot time!  =)

AT commands come from the hayes modem commands. ATZ is the command the resets the modem. This ATZ is here a test to see if your modem responds with OK. The garbage that you see comes from the usb-modem still sending stuff to you computer and does not respond to your commands. You can disconnect the modem physicall or by software to enforce a restart.

^M stands for linefeed or carriage return (can't remember which one) it is the one windows uses for textfiles and linux doesn't. In your chat output has double ^M^M can't recall that to be significant, but it's odd.

---

### Post by jwauton on 2010-02-06
Thank you for your prompt reply. The problem sounds more like hardware, either the modem itself or the USB port. I will try connecting to the other set of USB ports to see if it makes a difference.

---

### Post by puppywhacker on 2010-02-06
I don't think changing the USB ports will help, the problem is in the design of the device. It uses serial (like in ancient RS232 com-port serial) over USB and that has been always difficult to control, when it works it works fine, but when the communication is out of sync, it has very little controls to fix. We're talking last century technology here. Removing the stick and waiting a few seconds for the stick to settle before using it willmake your stick workable.

---

### Post by jwauton on 2010-02-07
Thanks for the info. As you say no change with USB. This is actually the Neotel integrated phone/modem combo BC2703 CDMA 800 EVDO Deskphone. Beginning to think the problem is with the phone itself. Am trying to get hold of Neotel to see what they say. In the meantime, is there anyway of sending a 'reset' to the phone to clear it?

---

### Post by jwauton on 2010-02-27
Reported problem to Neotel, and they eventually decided it could be a harware problem with the device, so they arranged to swap it out. Unfortunately, the problem is still there, so looks like it is not hardware after all. What next?

---

### Post by jwauton on 2010-03-24
The problem persists, so I have wired up a relay to switch the USB signals to phone on and off, controlled by the parallel port. Works nicely if I run it manually. 
 
The question is, where would I call this program from to automatically detect when there is a problem, and therefore reset the phone?
 
Thanks,
John

---

### Post by aquavitae on 2010-03-24
I'm having exactly the same issue - I think its just their devices.  How does your switch work?  Is it a physical switch you're wired up, or just a program? In theory you should be able to reset it using a simple command and I seem to remember seeing it somewhere once, but now of course I can't find it!  The bash script I saw also had a way of automatically resetting it if the connection was dropped.  If I find it I'll post the link.

---

### Post by aquavitae on 2010-03-24
I've found a long thread on the subject: [http://mybroadband.co.za/vb/showthread.php?129619-Neotel-working-on-Linux!]("http://mybroadband.co.za/vb/showthread.php?129619-Neotel-working-on-Linux!") and an article which gives a script to reset the modem: [http://mycapetown.biz/blog/]("http://mycapetown.biz/blog/"). The general idea is that reloading the uhci_hcd module will reset it, so in short:
```

sudo modprobe -r uhci_hcd
sudo modprobe uhci_hcd

```
I'm going to have a look at it tomorrow and see if I can figure out a good way of getting it to do it automatically when the connection is dropped.

---

### Post by jwauton on 2010-03-25
Circuit was basicly a 4 pole nc relay connected to D0 on the parallel port via an NPN transistor switch. Program outputs 01h to parallel port, waits 500mS then outputs 00h and waits 1Sec before exiting. Relay switches all 4 USB lines.
 
I just need to know how and where to call this program. Thinking maybe a cron script checking to see if line is working or not.

---

### Post by aquavitae on 2010-03-26
How do you connect? Do you do it manually by typing the pon command, or have you added it to the interfaces?  I added a ppp interface to /etc/interfaces, which brings up the connection automatically.  In theory, doing this would allow you to tell it to run a post-down script, i.e. when the connection is lost, but I haven't had any luck doing this so far. The other option would be to write a simple daemon-like script which runs in the background and checks every 30s or so whether the connection is still active.

I haven't had any time yet, but I'll have a go at it this weekend.

---

### Post by jwauton on 2010-03-26
It is brought up automatically. I tried a post-down script but it looks like the link is not actually dropping. The script never executed. This is why I think I need to check the log for lines with the garbage and then reset the USB.

---

### Post by jwauton on 2010-04-05
Still don't know what causes it, but finally have a work around. I now have a cron script which checks every 5 minutes for the rogue data string in the messages file. If this exists, then it runs the program that opens the relay on the USB port to reset it.

---

