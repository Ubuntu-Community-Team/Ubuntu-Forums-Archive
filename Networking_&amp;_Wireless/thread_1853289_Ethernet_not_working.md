---
title: "Ethernet not working"
date: 2011-10-02
forum: Networking &amp; Wireless
---

### Post by Lepard on 2011-10-02
I have a Zotac MAG HD-ND01-U that has a MCP79 Ethernet port.  With the official Ubuntu 11.04 32-bit release I am able to use the internet right after installing the OS.  However, in trying Lubuntu 11.04 I am unable to do so (either via install or liveCD).

- The Ethernet port does work in any other OS i try it in.
- I restarted the router.
- Forcedeth is being loaded (should work at this point)

I have searched the forums and used Google but have not found a solution to this problem.

Any ideas?

Thanks in advance.

---

### Post by papibe on 2011-10-02
I setup the exact same machine for my brother. I installed Ubuntu desktop 10.04 and XBMC. Great HTPC!

The very first thing we did was upgrade the BIOS. I've read some topics on the XBMC forums that recommended it.

I hope that helps,
Regards.

---

### Post by Lepard on 2011-10-02
Thanks for the suggestion, papibe. Unfortunately, that was also the first thing I did when I got the little machine a couple of weeks back.

---

### Post by papibe on 2011-10-02
Sorry to hear that.

Does it have 2Gb of RAM? I think 11.04 using Ubuntu Classic (Gnome 2.x) with no effects, would work very well as a regular desktop too.

Any reason 11.04 is not working for you?

Just some thoughts,
Regards.

---

### Post by Lepard on 2011-10-02
It actually has 4GB of RAM and I did not want to use Ubuntu (GNOME) because i've had a great run with Lubuntu on a work netbook (regular Acer Aspire with 1GB of RAM).

Funnily enough Ubuntu 11.04 does detect my network card and I get internet access using the liveCD and install.

Any thoughts?

---

### Post by Lepard on 2011-10-04
Just tried Ubuntu Mint (LXDE) and it has the same issue, so it's definitely related to the LXDE builds since the parent build (Unity/GNOME) detects the network card just fine.

---

### Post by Lepard on 2011-10-08
Lubuntu Beta 1 and Beta 2 have the same issue as well.

Any ideas on how to "change the driver" to get this machine online?  If Ubuntu does not have an issue with it, it has to be a bad driver call.

---

### Post by papibe on 2011-10-08
I have an idea. I'm not 100% sure it will work, but it involves installing a basic Ubuntu install, and then adding Lubuntu on top:

The general method is described [here]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall").

Basically,  you get what is called an installation minimal CD [here]("https://help.ubuntu.com/community/Installation/MinimalCD"). Then following this nice [tutorial]("http://www.psychocats.net/ubuntu/minimal"), you install a basic Ubuntu command line version.

Then you boot your machine and you'll get a text mode login screen. Note that because of a bug, you may boot into a black screen, but pressing Ctrl+Alt+F1 solves it.

Then you install the Lubuntu environment using apt-get.

I hope this works for you.
Regards.

---

### Post by Lepard on 2011-10-09
> **papibe said:**
> I have an idea. I'm not 100% sure it will work, but it involves installing a basic Ubuntu install, and then adding Lubuntu on top:

The general method is described [here]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall").

Basically,  you get what is called an installation minimal CD [here]("https://help.ubuntu.com/community/Installation/MinimalCD"). Then following this nice [tutorial]("http://www.psychocats.net/ubuntu/minimal"), you install a basic Ubuntu command line version.

Then you boot your machine and you'll get a text mode login screen. Note that because of a bug, you may boot into a black screen, but pressing Ctrl+Alt+F1 solves it.

Then you install the Lubuntu environment using apt-get.

I hope this works for you.
Regards.


Thanks, i'm definitely going to try this and hopefully it works out.

---

