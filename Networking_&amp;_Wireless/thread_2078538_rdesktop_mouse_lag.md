---
title: "rdesktop mouse lag"
date: 2012-10-31
forum: Networking &amp; Wireless
---

### Post by MatthewFordHB on 2012-10-31
Hi all,

I've been trying to use rdesktop as an RDP client for some thin clients in my organisation. The system uses lubuntu as a base and runs a sh script on boot with the rdesktop command in it.
The mouse works fine most of the time but when drag-selecting a large amount of data and moving the mouse to scroll down, the data seems to get "locked" scrolling and continue to scroll even after the users hand is removed from the mouse. This only seems to occur when there is a lot of data on the screen. A copy of my rdesktop command is below, I have tried with the -z flag and without, with no change. The server is running Windows Server 2008 R2 Enterprise and works absolutely fine with Windows RDP.

rdesktop -f -N -r disk:USB=/media -d mydomain -u "" -p "" -x l -r sound:local myserver;

I really hope someone is able to help as I've been getting very frustrated over this, thank you in advance.

---

### Post by SteveDee on 2012-11-03
> **MatthewFordHB said:**
> ...The mouse works fine most of the time but when drag-selecting a large amount of data and moving the mouse to scroll down, the data seems to get "locked" scrolling and continue to scroll even after the users hand is removed from the mouse....

I'm running approx 80 Lubuntu based thin clients in our organisation, in addition to the remaining 25-30 HP thin clients which are slowly being replaced. Although the Lubuntu TCs are running on a motley selection of old & feeble desktops & laptops, they boot faster and run with less maintenance calls than the HPs.

I haven't noticed the problem you mention, but will try to test for this when I'm back at work this week.

The command line I use does not include USB as we try to discourage our staff from using USB memory/drives on our network. So, as a test, I'd encourage you to step up to a Linux machine and try this:-
```

rdesktop -d {domain} -u {default user} -f -n {client name} -r sound:local {server name}

```
...thus leaving out USB and "N" (which I thought I'd read somewhere could create some kind of problem).

Also, can you give me a better idea how to recreate your problem? Are you saying when you have a Word document open, you select (say) 100 lines, then try to drag it to another area of the document, or to another application?

The only problem we do have (which could be related) is playing videos. These often appear jerky, and performance is even worse on the HP TCs, presumably because they have less RAM. 

This was not a problem when we were still running Citrix, and I understand its a general problem with Microsoft RDP. MS have tried to get around this with the feature "RemoteFX". Unfortunately we have not been able to get this going up to now due to work-load & priority constraints.

Oh, another question: which version of Lubuntu are you using?

---

### Post by MatthewFordHB on 2012-11-20
Thanks for your response. I have tried with many variations of the rdesktop command, including without the USB and -N as I also thought that was the problem, with no luck...

The problem occurs when selecting and dragging the mouse to scroll the window while selecting. It is as if the mouse gets stuck and it is impossible to stop the window from scrolling...

The video problem is no issue for us as we do not encourage staff to watch videos anyway, as a note however I have only found that it occurs with flash, HTML5 video seems to perform reasonably well. I hope this is enough information, let me know if you need to know anything else.

EDIT: I have since posting this found that the problem is linked to a bug with Xorg where it takes 100% CPU when scrolling ANY window, even outside Ubuntu.

---

