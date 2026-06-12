---
title: "Network Manager Stopped Recognizing Wireless Network"
date: 2011-01-24
forum: Networking &amp; Wireless
---

### Post by writingboy on 2011-01-24
I am a Windows refugee who discovered Ubuntu as a way to save my files from my virus-ravaged computer. Had no installation discs for Windows, so when I had to wipe my hard drive and start over, I decided to give Ubuntu a try. I've had mixed success, but that's another post...

Right now, the problem is that I installed 10.10 two weeks ago and was able to connect to the Internet with no problems - until yesterday. Suddenly, our wireless network (the only one in the vicinity) does not come up as available in Network Manager. In fact, the entire wireless option disappeared. I know there are many posts and threads on here about this, but weeding through them trying to find an answer is more frustrating than actually dealing with the problem. I know the router works because I can post on this forum from the Macbook. I really like Ubuntu and would like to keep using it, but not being able to connect to the Internet now on top of the other issues I've had is making me doubt I want to continue down this Linux road. Does anybody have a simple solution that doesn't involve a lot of coding, as I'm rather new to all this? Thank you so much in advance.

Mike

P.S. When I attempted an analysis through System Testing, it said something about there being no proprietary drivers?

---

### Post by grahammechanical on 2011-01-24
Hi

1) If, until recently you had internet access using a wireless connection then we can assume that the drivers built into the kernel are working with the wireless adapter in your machine. Do not get confused about not having proprietary drivers installed. Some users have ethical issues about using proprietary software and for this reason they are not installed unless you decide to install them.

2) Can you see a network icon? What information do you see when you left click and right click the icon?

3) A right click of the icon will produce a drop down menu and you will see Enable Networking and Enable Wireless. Are there tick marks against both lines? If not, then select each line and click on it. Clicking on the line Enable Networking is a way of switching networking off and on. It is the same with the line Enable Wireless. Is networking switched on? Is wireless switched on? You need to answer these questions.

4) Are you using a laptop? With a netbook and a laptop the user can switch the on-board wireless adapter off and on using a keyboard key combination. Does the wireless adapter need to be physically activated, switched on?

5) Is there a feature in the BIOS that allows you to disable the wireless adapter? Is wireless disabled in the BIOS settings? This was the reason someone was having problems just the other week.

Finally, please understand and accept that I do not care if you do not continue using Ubuntu and Linux. As we say in England, it is no skin off my nose. So, please do not talk like that. It sounds like some kind of threat and it puts me off from offering advice.

Regards.

---

### Post by writingboy on 2011-01-24
Thank you for your response, grahammechanical. No threat intended - just venting some frustration. Two weeks of constant computer problems has me weary! :)

1) Thank you for the clarification about proprietary drivers. I'm taking it to mean that they're not something I need to access the wireless network, and certainly Network Manager worked until yesterday, so I assume the kernels are still there and should be working.

2) Yes, the network icon is present. When I left-click, it says:

Wired Network
    disconnected

VPN Connections >

Right-clicking brings up:

Enable Networking
Enable Notifications
[Connection Information] - greyed out
Edit Connections
About

3) I do have a tick mark on Enable Networking, but there is no Enable Wireless prompt available, so it can't be tick-marked...

4) No, I am using a desktop with a wireless LAN PCI card (a Rosewill RNX-N300X, in case that info's needed).

5) I had read on the forum about enabling the wireless adapter in BIOS, but that does not appear to be an option in mine. My desktop is from 2006 - could that setting just not have been a possibility "back then"?

I do appreciate your asking these questions, because I know it will assist in the process of elimination. As a sort of update, I plugged in my old USB adapter (which was replaced with the PCI card months ago when it stopped working), and Network Manager recognizes *it*, but only briefly before it boots me off-line again. I was able to download the WICD package, which I had read was an option, but that isn't picking up a network, either. It made me wonder if there's also a possibility my few-months-old PCI card gave out already?

---

