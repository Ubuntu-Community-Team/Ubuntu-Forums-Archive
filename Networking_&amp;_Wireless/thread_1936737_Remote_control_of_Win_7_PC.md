---
title: "Remote control of Win 7 PC"
date: 2012-03-06
forum: Networking &amp; Wireless
---

### Post by LinuxBob on 2012-03-06
I'd like to be able to remotely access and control a Win 7 PC in order to start a Pandora session on the Win 7 PC, not on the remotely accessing Ubuntu 10.04 PC.  I want to do this because the Win 7 PC has wireless audio transmitter set up as speakers and Pandora is thereby transmitted to each stereo receiver throughout the house.  The USB xmttr is out of production and I only have one left. I need the transmitter on the Win 7 to broadcast the audio from MLB.tv, VUDU and other similar Internet video streaming applications.  My wife is used to starting Pandora from the Ubuntu machine to which until recently the transmitter had been attached, a physical location issue.

Remote desktop does not work for a couple of reasons.  First and foremost, Win 7 PC is using home premium which cannot serve as RDP host.  Second, the ky feature I need is for the Ubuntu user to be on the Win 7 PC turning on the Win 7 audio directly, not having the Win 7 audio come to the Ubuntu client via ethernet.

What can do this inexpensively?  PCAnywhere? VNC?  GotoMyPC?  I am not worried about interrupting a session on the Win 7 host as it mainly serves to feed Xbox media center extenders.

---

### Post by BWGreg on 2012-03-07
Team Viewer 6 is available for Ubuntu and you can install the latest Team Viewer on your Win 7 PC. You will be able to access your Win 7 PC from your Ubuntu one, but not vice versa. If you ever want to access Ubuntu from your Win 7 PC, I believe you need to uninstall TV 7 and install TV 6 on the Win 7 PC.

---

### Post by Sergius14 on 2012-03-07
There already are TeamViewer 7...

And you can control your Ubuntu from a Windows Machinne.

On TeamViewer6 on Linux there was an odd bug that you have a screen resolution divisible by 4.

1366 / 4 = bad

1360 / 4 = good

(I think, didn't try yet that this bug is solved in TV7).

Regards,

---

### Post by BWGreg on 2012-03-07
:D
 
I see that now. Wonder why I did not the first time I looked. Maybe because it is beta?
 
Edit: I installed it, but still cannot remote from Win7 to Ubuntu, but mute point in this topic. Thanks though! I probably just need to downgrade my TV7 on WIn 7 to an older version.

---

### Post by LinuxBob on 2012-03-07
I don;'t need Win 7 Professional?  Home premium does not allow Windows to the remote desktop server.

---

### Post by Sergius14 on 2012-03-08
With TeamViewer 7 you just can remote any Windows version from your Ubuntu for free (non-comercial).

From Windows you could also remote control an Ubuntu PC, althow not always is very happy (you may get a black screen for ex.), it's expected to work out of the box.

TeamViewer relies on their own remote desktop technology and has no relation to RDP or others (VNC).

---

