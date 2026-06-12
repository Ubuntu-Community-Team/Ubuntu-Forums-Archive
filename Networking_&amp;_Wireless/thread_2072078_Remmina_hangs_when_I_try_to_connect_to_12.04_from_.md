---
title: "Remmina hangs when I try to connect to 12.04 from 12.04 via VNC"
date: 2012-10-17
forum: Networking &amp; Wireless
---

### Post by vaguely_clear on 2012-10-17
First: I'm not sure that I'm posting to the correct forum. Apologies in advance for that.

I have two machines, both running Ubuntu 12.04. One is a normal desktop connected to my network via WiFi. The other is an older desktop running headless and on a wired connection to the same LAN.

I use the headless machine as a light home server for storage and the like. I would like to be able to manage it on my main machine via VNC (or something similar), but I've had limited success. It worked for awhile using Remmina, but now, when I try to connect to the headless machine, Remmina (and all other clients I've tried) just hang on the "Connecting" dialog (see attachment).

I know that the network is working okay, because I have an SMB share on the headless machine that is mounted every time the other machine boots, and I can still access and modify files on that share.

I've found that if I force the headless machine to shut down and reboot it, I can access it for awhile. Eventually, though, the connection dialog will start stalling and I haven't identified any activity that gets me to that point, other than closing the VNC connection and trying it again awhile later.

I'm at a loss. Where should I go from here? Is there an error log somewhere that I could post?

---

### Post by vaguely_clear on 2012-10-17
Well, my limited abilities haven't gotten me much further. I'm pretty sure it's not the VNC client software. I've tried Remmina, Vinagre, xvnc4viewer, and something else the name of which escapes me. All essentially behave the same: they try to connect, but just sit there trying. Attachments 1 shows this happening with xvnc4viewer.

I tried forcing a shutdown on the server and restarting. Attachment 2 shows Vinagre trying to connect after the restart. What happened now? That error message is new. Remmina is failing after the restart as well.

I keep reading about port 5900. Do I need to port forward this on my router? FYI, I'm doing this on a local LAN without SSH and I have no plans to make this available over the internet.

I'm off to restart my client machine and see if that helps. Anybody have suggestions? I'm frackin' lost.

---

### Post by vaguely_clear on 2012-10-18
Just rebooted my client machine and tried to connect: no go. I guess I'm going to have to scrape up a spare monitor and see what's up on the server. Dang.

Any ideas? Anybody?

---

### Post by vaguely_clear on 2012-10-19
New thought: I have experienced generally low speeds on my home network for the past few days and I'm not sure whether it's the router or my internet connection. Is there something I can check/test on my router to eliminate network issues as the problem with my VNC? I have DD-WRT running on my Buffalo router.

<throws rock and listens for echo>

Man, it's quiet in here. I feel like I'm talking to myself. :(

---

### Post by vaguely_clear on 2012-10-20
Shameless Bump.

---

### Post by steeldriver on 2012-10-20
I notice your original connection dialog has both IP and an unqualified hostname - which are you actually specifying when you set up the connection? If your local hostname resolution relies on avahi and that's got screwed up somehow (possibly hinted to by the recent popup) then it may not be getting the right IP

You could possibly confirm all's well on that front by pinging the hosntame and checking it responds with the expected IP?

Beyond that I would SSH into the server and start poking around there - the VNC connection log should be in ~/.vnc/*hostname*:*display*.log or somesuch - you can also use ps to check that the VNC server really is running, check UFW status, netstat to confirm LISTEN on 5900 etc.

---

### Post by vaguely_clear on 2012-10-20
Thanks for all the info, steeldriver!

> **steeldriver said:**
> I notice your original connection dialog has both IP and an unqualified hostname - which are you actually specifying when you set up the connection? If your local hostname resolution relies on avahi and that's got screwed up somehow (possibly hinted to by the recent popup) then it may not be getting the right IP

You could possibly confirm all's well on that front by pinging the hosntame and checking it responds with the expected IP?

I believe Remmina is using the IP to connect (that's what I entered under "Server" in the settings; IAN-SERVER is just the name of the connection). I used Network Tools to verify that the host name/IP are related. I believe everything is okay on that front. Just for clarity, IAN-SERVER is the unqualified hostname, yes?

> **steeldriver said:**
> Beyond that I would SSH into the server and start poking around there - the VNC connection log should be in ~/.vnc/*hostname*:*display*.log or somesuch - you can also use ps to check that the VNC server really is running, check UFW status, netstat to confirm LISTEN on 5900 etc.

I'll have to wait until next week when I have a spare monitor to run on the server, as SSH is not set up on it at the moment. Everything you listed here is to be done on the server and requires SSH, correct?

EDIT: I just used netstat on the server's IP from my workstation. It doesn't list port 5900. That's probably due to VNC not running on the machine, yeah?

EDIT AGAIN: Forgive me, I used Port Scan on my server's IP.

---

### Post by steeldriver on 2012-10-20
Ah my mistake, I'm not familiar with the remmina interface - if 'IAN-SERVER' is just the connection name ignore my comments about hostnames

Yes you would need to use SSH if direct VNC isn't working (and if SSH isn't working then yes you would need a real physical connection)

FYI I don't *think* netstat tells you anything other than remote ports that you're actually connected to, which you're obviously not in this case - you could install nmap and do a proper port scan with that

```
sudo apt-get install nmap

sudo nmap -A -T4 *your-server*
```

---

### Post by vaguely_clear on 2012-10-20
> **steeldriver said:**
> Ah my mistake, I'm not familiar with the remmina interface - if 'IAN-SERVER' is just the connection name ignore my comments about hostnames

Yes you would need to use SSH if direct VNC isn't working (and if SSH isn't working then yes you would need a real physical connection)

FYI I don't *think* netstat tells you anything other than remote ports that you're actually connected to, which you're obviously not in this case - you could install nmap and do a proper port scan with that

```
sudo apt-get install nmap

sudo nmap -A -T4 *your-server*
```

nmap was actually required by Network Tools to perform a port scan. I also ran it in the terminal per your command and it showed me the same ports for the server, none of which were 5900.

Time to get a monitor hooked up, I suppose.

---

### Post by steeldriver on 2012-10-21
were there any other low-number 590x ports? the default is for it to assign the port based on the X display number as '5900 + display' so  5900 is what you see when you're connecting to the primary display (the usual single-user 'desktop sharing'  scenario) but if you are running truly headless with multiple sessions 'your' session may be on (say) display :5 with corresponding port 5905

---

### Post by vaguely_clear on 2012-10-21
Well, I impatiently connected my workstation monitor to the server and found that it wasn't starting up all the way. It was stuck on the low graphics mode screen and I couldn't get past it. After some cleaning and updates, though, the server machine is running fine (I think). 

> **steeldriver said:**
> were there any other low-number 590x ports? the default is for it to assign the port based on the X display number as '5900 + display' so  5900 is what you see when you're connecting to the primary display (the usual single-user 'desktop sharing'  scenario) but if you are running truly headless with multiple sessions 'your' session may be on (say) display :5 with corresponding port 5905

Hmmm, interesting. Could you direct me to a more detailed explanation of what you're talking about? I'm not entirely clear what constitutes a "session".

There are no low number 590x ports listed on netstat. However, 5900 is listed twice, as follows:

```
tcp    0.0.0.0    5900    LISTEN
tcp6   ::         5900    LISTEN
```

Would that be causing any trouble?

I tested VNC functionality from a MacBook and everything seems to be working, but I have a feeling I will encounter this again. I'm off to return my workstation monitor and give it a shot from there.

---

### Post by vaguely_clear on 2012-10-21
Whoa - I think I just witnessed the problem. I was monitoring active processes via System Monitor when I got a apport error dialog. The process vino-server then disappeared from the Processes list. Clearly the Vino VNC server is crashing.

So, any suggestions for alternative VNC software?

---

### Post by vaguely_clear on 2012-10-21
Everything is put back together and VNC seems to be working right now. SSH is working via PuTTY, so I guess I'll SSH into the server if vino-server fails again.

I also installed freenx-server on the server machine and hoped to try it on my workstation. So far, though, the NX plug-in for Remmina has yielded nothing. It starts up a window, then gives me the error "Failed to load session "gnome-fallback"" before exiting. Maybe I'll try another NX client. Or maybe I need to forward port 22?

The ideal solution would obviously be to figure out why Vino is crashing and fix it, but I've had no luck on that front.

---

