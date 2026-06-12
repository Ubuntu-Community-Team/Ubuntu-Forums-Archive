---
title: "QuickSynergy doesn't execute"
date: 2012-03-12
forum: Networking &amp; Wireless
---

### Post by Odyssey1942 on 2012-03-12
I have followed the GUI instructions found here:

[https://help.ubuntu.com/community/SynergyHowto](https://help.ubuntu.com/community/SynergyHowto)

but cannot get the program to function (i.e. show me the client screen)

Just to ensure that I understand the instructions (they are a little hard to follow):

The controlling computer is known as the "Host", also the "Server", and is the computer with the mouse & keyboard.

On the "Clent" computer/s, which is/are to be controlled by the Host/Server computer, nothing is typed in the "Share" tab. In the "Use" tab, the IP# (alternatively, not in addition to, hostname with .local added to the hostname) of the Host/Server computer is entered in the box labeled "Server hostname/IP address". I have tried IP#, and hostname with and without .local attached.

In the box labeled "Screen name:", enter the hostname of the Client computer (presumably without the .local as it is not mentioned in the instructions) [I have also tried it with the .local added]

On the Host machine, all IP#'s (or hostnames) of client computer/s is/are entered in the "Share" tab, and no entries are made in the "Use" tab. (I am using IP #'s since there is no ambiguity, but have also tried the hostname of the client computer, with and without .local added to the hostname.)

When I click "Execute" everything goes grey (on both computers) except the buttons at the bottom which now show as "About, "Stop" and "Close". I do not know whether QuickSynergy is attempting to communicate, but I assume that whatever is happening is incomplete because if I move my mouse to the appropriate edge of the screen, the screen does not change to the client computer.

I can ping each computer from the other, and reach each from the other at Places/Network so I assume that communication between the computers is not an issue.

I have not gone past the GUI portion because it quickly gets above my level of experience and understanding.

Can anyone see in the above anything that I might be doing wrong compared to the above referenced guide? Thanks.

---

### Post by Odyssey1942 on 2012-03-13
Anyone had any experience with QuickSynergy? Thanks.

---

### Post by Odyssey1942 on 2012-03-14
Synergy then?

---

### Post by scatteredstones on 2012-06-06
I am by no means an expert, but I can tell you how I have mine set up. 

1. Host - Share tab  with hostnames of other pcs.
2. Clients - hostname of Host only.

Couple of additional notes - I have never been able to get this to work wirelessly. Also, I have discovered that it matters which tab is open when you execute. I don't know why, but when I have my Share tab up on my client and execute, QS does not work. The Use tab has to be active.

---

