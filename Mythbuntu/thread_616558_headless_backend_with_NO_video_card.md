---
title: "headless backend with NO video card"
date: 2007-11-18
forum: Mythbuntu
---

### Post by pasta514 on 2007-11-18
My backend machine will sit in the garage with no chance of plugging in a KB/monitor.  

Everything was working fine (in the house, during setup), so I yanked out the video card and rebooted.  Then I SSH'd into the machine without problem.  Then 
 sudo shutdown -h now

Now when I power on the machine the ethernet port appears to be dead.  No blinky lights, no ping.

Was planning to manage this machine through the remote frontend, SSH or XDCMP

Assume I have to put the card back to solve the problem, but going ahead what should I do to allow me to yank the card?

---

### Post by uopjohnson on 2007-11-18
Honestly, I'm surprised that your bios would even boot with no video card.  Is there a reason not to get a $20 one and leave it in? That would be the easiest way to solve this.  Otherwise you are going to have a very difficult time diagnosing the problem since you can't see anything when it happens.

---

### Post by road2elysium on 2007-11-18
> **uopjohnson said:**
> Honestly, I'm surprised that your bios would even boot with no video card.  Is there a reason not to get a $20 one and leave it in? That would be the easiest way to solve this.  Otherwise you are going to have a very difficult time diagnosing the problem since you can't see anything when it happens.

I agree with the above.  If you don't have integrated graphics on your mobo, even headless administration via SSH/VNC would be problematic.  I would leave some sort of video card in for that purpose alone.

---

### Post by pasta514 on 2007-11-18
well, turns out my no boot problem is not related to the lack of video card.  Made a stupid error which I disconvered when moving the card back into the machine.  It boots without the card, just 4 beeps during post.  No problem with SSH.  

I'm curious now why a card would be needed if the gui is being exported via XDMCP?  I agree VNC will not work without it.   If necessary I might install webmin as an alternative.

---

### Post by uopjohnson on 2007-11-18
The video card isn't necessary it is just very nice to have.  Think about the amount of time it just took you to move it back and forth to check whatever this small error was.  At some point you will have an ethernet cord come loose, or a dhcp failure and you will once again need to log directly into the frontend and check it out. 
It is really a matter of convenience, not necessity.

---

### Post by kvonb on 2007-11-20
-

---

### Post by mellowd on 2007-11-20
Some motherboards simply wont boot without a video card. Yours seems to boot though. I'd just leave the cheapest one I could find in there for convinience

---

### Post by Cohh on 2008-03-18
are there any programs or utilities that can emulate an X session without a video adapter for VNC purposes?

---

### Post by ian dobson on 2008-03-18
Hi,

Do you really need to use VNC? Although I have a montor/keyboard on the server/backend I find it easier to create a remote X session.

I can even run an X session from my XP based laptop:-
1) Install the xauth package on the remote system (server)
2) On the local system install the Cygwin package including the openSSH package.
3) Start an xterm session on the local system (startxwin.bat)
4) Start a ssh connection to the remote system with X redirection enabled (ssh -X - Y user@IP_address)

I only really need X to run mythtv-setup on the backend, but it's enough for me.

Regards
Ian Dobson

---

### Post by mungewell on 2008-10-09
> **Cohh said:**
> are there any programs or utilities that can emulate an X session without a video adapter for VNC purposes?

yes: xvfb = Virtual Framebuffer 'fake' X server

Mungewell.

---

