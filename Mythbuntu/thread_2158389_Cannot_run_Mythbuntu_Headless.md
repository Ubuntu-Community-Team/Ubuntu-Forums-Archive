---
title: "Cannot run Mythbuntu Headless"
date: 2013-06-28
forum: Mythbuntu
---

### Post by MmikeyZ on 2013-06-28
When I boot my machine without a monitor attached it doesn't boot to desktop. Instead when I plug a monitor in its on a cmd line login interface 

"Ubuntu 12.04.2 LTS BACKEND tty1 
BACKEND login: "

I want to have the box sitting in a cupboard out back without monitor/keyboard/mouse and interface with VNC. 

I've tried installing as f/end with b/end, b/end only, and also tried installing updates. They all make no difference.
I've tried looking through bios to find anything to do with booting without monitor with no luck.
I can putty to the machine but I'd prefer to VNC.
When I do connect through VNC it says it is actively refused.

Please help, I've searched through forums and there probably is an answer to this but I cannot find it.

---

### Post by AxelVK on 2013-06-29
I have exactly the same problem. Asked here in these forums and only got one response which didn't work. Searched and found some other suggestions but none has worked so far. To be honest, I'm a little disappointed with Linux. They say "try Linux, its great". I did and I can't find answers to problems. This particular problem would have been a piece of cake with Windows. Part of the problem for me is that a lot of people who is trying to help seem to assume that everyone already knows Linux inside out and knows how to install packages, deal with install and permissions issues, check logs and interpret messages, etc. Some people won't like me saying this but that has been my genuine experience with Linux.

---

### Post by Akriss on 2013-06-29
Have you guys tried the "startup behavior" section within the "Mythbuntu control center" and set it to auto log you on?

It works for my headless Backend just fine.

Hope it helps.

---

### Post by jimp180 on 2013-06-30
> **Akriss said:**
> Have you guys tried the "startup behavior" section within the "Mythbuntu control center" and set it to auto log you on?

It works for my headless Backend just fine.

Hope it helps.

I am curious if this works for you guys? I have used mythbuntu for a long time and have always had it set to auto login and that works (or so it did thru 11.10). My master backend isn't exactlyu headless but I run it through a KVM switch and am ussually connected to another computer so when I loose power it boots as if it where headless and always did fine, but I don't beleieve that to be the case since I installed 12.04 because I too have seen the console login when I switch back to it now after a power interuption. It is just one of those things in the later builds of Mythbuntu that the developers have gotten to busy to worry about, it's like now they make it all the same as ubuntu and don't care that its meant for a dedicated purpose. For example, I've always used webmin to do my updates remotely, never ever had a problem with that, but now all of a sudden with this newest release nearly every time I turn a TV on in the house I have a "update Manager" screen showing me I have updates. These are dedicated frontends, I dont have or want mice and keyboards connected to them but now I need this because I cant watch TV with a big update screen all in the middle. That even goes for the install, I have a dual opteron board with plenty of power to run a master backend, it's been doing so for the last 5 years fine. It's a server board, therefore it has no PCIE slots, all it has is PCI and PCIX slots and for the last 5 years I used the onboard video, BECAUSE ITS A SERVER, I don't need massive powerful graphics on the bckend. But in order to even install 12.04 I had to find a rare PCI card that would satisfy the higher resolution that the install program needs now!

---

### Post by tgm4883 on 2013-06-30
> **jimp180 said:**
> I am curious if this works for you guys? I have used mythbuntu for a long time and have always had it set to auto login and that works (or so it did thru 11.10). My master backend isn't exactlyu headless but I run it through a KVM switch and am ussually connected to another computer so when I loose power it boots as if it where headless and always did fine, but I don't beleieve that to be the case since I installed 12.04 because I too have seen the console login when I switch back to it now after a power interuption. It is just one of those things in the later builds of Mythbuntu that the developers have gotten to busy to worry about, it's like now they make it all the same as ubuntu and don't care that its meant for a dedicated purpose. For example, I've always used webmin to do my updates remotely, never ever had a problem with that, but now all of a sudden with this newest release nearly every time I turn a TV on in the house I have a "update Manager" screen showing me I have updates. These are dedicated frontends, I dont have or want mice and keyboards connected to them but now I need this because I cant watch TV with a big update screen all in the middle. That even goes for the install, I have a dual opteron board with plenty of power to run a master backend, it's been doing so for the last 5 years fine. It's a server board, therefore it has no PCIE slots, all it has is PCI and PCIX slots and for the last 5 years I used the onboard video, BECAUSE ITS A SERVER, I don't need massive powerful graphics on the bckend. But in order to even install 12.04 I had to find a rare PCI card that would satisfy the higher resolution that the install program needs now!

Can I get a paragraph break?

I have a headless Mythbuntu backend running 12.04 just fine. It uses the onboard video and it logs in automatically. When I want to VNC into the machine, I first SSH into the box and start VNC, then I VNC directly to the already logged in interface.

As for the installer, it works on a 800x600 screen, so if your server can't handle that then I'm not sure what to tell you.

Oh, and please link to any bug reports for the issues you are having.

---

### Post by MmikeyZ on 2013-07-01
I'll attempt tgm4883's method tonight. I have tried enabling auto login in the control center but the option isnt available. Here's a [link]("http://askubuntu.com/questions/65957/how-do-i-enable-automatic-login-in-mythbuntu-11-10") to someone else who had the problem enabling auto login.

---

### Post by MmikeyZ on 2013-07-01
tgm4883 are you able to tell me how you start vnc from the cmd line? I've tried sudo x11vnc but it fails "XOpenDisplay(":0") failed." Please forgive me for posting my output below, I've tried to find instruction as to where to post logs without any luck.  

So to confirm I can start the machine headless and putty into it. However I cannot start vnc once I'm in.

Seems like a common issue, hopefully we can come to a solution.


01/07/2013 22:13:18 x11vnc version: 0.9.12 lastmod: 2010-09-09  pid: 2270
01/07/2013 22:13:18 XOpenDisplay("") failed.
01/07/2013 22:13:18 Trying again with XAUTHLOCALHOSTNAME=localhost ...
01/07/2013 22:13:18
01/07/2013 22:13:18 *** XOpenDisplay failed. No -display or DISPLAY.
01/07/2013 22:13:18 *** Trying ":0" in 4 seconds.  Press Ctrl-C to abort.
01/07/2013 22:13:18 *** 1 2 3 4
01/07/2013 22:13:22 XOpenDisplay(":0") failed.
01/07/2013 22:13:22 Trying again with XAUTHLOCALHOSTNAME=localhost ...
01/07/2013 22:13:22 XOpenDisplay(":0") failed.
01/07/2013 22:13:22 Trying again with unset XAUTHLOCALHOSTNAME ...
01/07/2013 22:13:22


01/07/2013 22:13:22 ***************************************
01/07/2013 22:13:22 *** XOpenDisplay failed (:0)

---

### Post by Akriss on 2013-07-01
Ya know there is setup options for VNC services within Mythbuntu control panel.

---

### Post by tgm4883 on 2013-07-01
> **MmikeyZ said:**
> tgm4883 are you able to tell me how you start vnc from the cmd line? I've tried sudo x11vnc but it fails "XOpenDisplay(":0") failed." Please forgive me for posting my output below, I've tried to find instruction as to where to post logs without any luck.  

So to confirm I can start the machine headless and putty into it. However I cannot start vnc once I'm in.

Seems like a common issue, hopefully we can come to a solution.


01/07/2013 22:13:18 x11vnc version: 0.9.12 lastmod: 2010-09-09  pid: 2270
01/07/2013 22:13:18 XOpenDisplay("") failed.
01/07/2013 22:13:18 Trying again with XAUTHLOCALHOSTNAME=localhost ...
01/07/2013 22:13:18
01/07/2013 22:13:18 *** XOpenDisplay failed. No -display or DISPLAY.
01/07/2013 22:13:18 *** Trying ":0" in 4 seconds.  Press Ctrl-C to abort.
01/07/2013 22:13:18 *** 1 2 3 4
01/07/2013 22:13:22 XOpenDisplay(":0") failed.
01/07/2013 22:13:22 Trying again with XAUTHLOCALHOSTNAME=localhost ...
01/07/2013 22:13:22 XOpenDisplay(":0") failed.
01/07/2013 22:13:22 Trying again with unset XAUTHLOCALHOSTNAME ...
01/07/2013 22:13:22


01/07/2013 22:13:22 ***************************************
01/07/2013 22:13:22 *** XOpenDisplay failed (:0)

Why would you run it with sudo?


I have a bash script I made that starts it. This is the contents.

```
#!/bin/bash
x11vnc -safer -localhost -nopw -display :0 -bg
```

Then I use remmina to create an SSH tunnel and connect to the VNC server.

---

### Post by MmikeyZ on 2013-07-01
@tgm4883 thanks again for the help. I'll quickly explain why I used sudo, Im a noob, therefore I  haven't got a clue what I'm doing. 

Firstly tried "[COLOR=#000000][FONT=Ubuntu Mono]x11vnc -safer -localhost -nopw -display :0 -bg" using putty and got the following error:[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR][FONT=arial]02/07/2013 08:07:26 -safer mode:[/FONT]
[FONT=arial]02/07/2013 08:07:26    vnc_connect=0[/FONT]
[FONT=arial]02/07/2013 08:07:26    accept_remote_cmds=0[/FONT]
[FONT=arial]02/07/2013 08:07:26    safe_remote_only=1[/FONT]
[FONT=arial]02/07/2013 08:07:26    launch_gui=0[/FONT]
[FONT=arial]02/07/2013 08:07:26 x11vnc version: 0.9.12 lastmod: 2010-09-09  pid: 2088[/FONT]
[FONT=arial]02/07/2013 08:07:26 XOpenDisplay(":0") failed.[/FONT]
[FONT=arial]02/07/2013 08:07:26 Trying again with XAUTHLOCALHOSTNAME=localhost ...[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]02/07/2013 08:07:26 ***************************************[/FONT]
[FONT=arial]02/07/2013 08:07:26 *** XOpenDisplay failed (:0)[/FONT]
[COLOR=#000000][FONT=Ubuntu Mono]
Secondly what do you mean by creating an SSH tunnel? Why do you connect with remmina, why not vnc, is there a specific reason?

Please excuse my noob questions, I just want to get to the bottom of this.[/FONT][/COLOR]

---

### Post by tgm4883 on 2013-07-01
> **MmikeyZ said:**
> @tgm4883 thanks again for the help. I'll quickly explain why I used sudo, Im a noob, therefore I  haven't got a clue what I'm doing. 

Firstly tried "[COLOR=#000000][FONT=Ubuntu Mono]x11vnc -safer -localhost -nopw -display :0 -bg" using putty and got the following error:[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR][FONT=arial]02/07/2013 08:07:26 -safer mode:[/FONT]
[FONT=arial]02/07/2013 08:07:26    vnc_connect=0[/FONT]
[FONT=arial]02/07/2013 08:07:26    accept_remote_cmds=0[/FONT]
[FONT=arial]02/07/2013 08:07:26    safe_remote_only=1[/FONT]
[FONT=arial]02/07/2013 08:07:26    launch_gui=0[/FONT]
[FONT=arial]02/07/2013 08:07:26 x11vnc version: 0.9.12 lastmod: 2010-09-09  pid: 2088[/FONT]
[FONT=arial]02/07/2013 08:07:26 XOpenDisplay(":0") failed.[/FONT]
[FONT=arial]02/07/2013 08:07:26 Trying again with XAUTHLOCALHOSTNAME=localhost ...[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]02/07/2013 08:07:26 ***************************************[/FONT]
[FONT=arial]02/07/2013 08:07:26 *** XOpenDisplay failed (:0)[/FONT]
[COLOR=#000000][FONT=Ubuntu Mono]
Secondly what do you mean by creating an SSH tunnel? Why do you connect with remmina, why not vnc, is there a specific reason?

Please excuse my noob questions, I just want to get to the bottom of this.[/FONT][/COLOR]

Remmina is a frontend for VNC. I use it because I connect to both Windows machines via RDP and linux machines via VNC and it's a convenient place to keep all this. Secondly, it's got built in functionality for SSH tunnels, so that is a plus. VNC is very insecure and a bad thing to be running all the time. An SSH tunnel makes it so you have to SSH to the machine, then you connect to the VNC server over SSH (the -localhost in the vnc command means it's only listening on localhost).

You're getting the error message because you don't have a display server running. You can either setup xorg.conf so it will allow a display server to be started (since it isn't starting in your case), or you could try something like the following when running x11vnc 

```
/usr/bin/x11vnc -safer -localhost -nopw -bg -shared -xkb -o /var/log/x11vnc.log
```

---

### Post by MmikeyZ on 2013-07-08
Gave up, ended up making dummy VGA plug.

---

### Post by Ubu_Fester on 2013-07-12
Try this at the command line:
x11vnc -forever -rfbport 5900 -rfbauth ~/.vnc/x11vnc.pass -o ~/.vnc/x11vnc.log -loopbg -display :0
(need to first setup a password for vnc)


I followed a tutorial (forgot where...).  But basically does the following:

created a shell script at:  ~/.config/autostart/x11vnc.sh

Which contains:



> #!/bin/sh


/usr/bin/x11vnc -forever -rfbport 5900 -rfbauth ~/.vnc/x11vnc.pass -o ~/.vnc/x11vnc.log -loopbg -display :0




---

