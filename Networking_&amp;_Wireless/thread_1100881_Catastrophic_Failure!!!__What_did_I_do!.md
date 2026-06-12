---
title: "Catastrophic Failure!!!  What did I do?!"
date: 2009-03-19
forum: Networking &amp; Wireless
---

### Post by GeistDev on 2009-03-19
I have an issue.  

(how many times has everyone here heard that? lol)

OK so I am using Ubuntu and have both GNOME and KDE4 environments installed.  I noticed after turning on the computer and going directly to a KDE4 session the Knetworkmanger did not always detect my wireless adapter (netgear wg111v2).  If I went into the GNOME session, it would be detected and at that point I could go back to KDE and be good to go.

I was planning to remove GNOME so I thought it'd be prudent to install a new network manager in KDE.  Using Adept, I installed K-lan, and in doing so it removed both KNetworkmanager and the Gnome network client.

K-lan did not do anything and I couldn't get it to recognize my wireless adapter, so I figured I'd go back to Knetworkmanager.

Using Adept, I uninstalled K-lan and... Knetworkmanger could not be installed because guess what, I was not connected to the internet ---DOUUH!

So now I have a Ubuntu desktop with Gnome and KDE4, with no network manager...and no internet.  How do I get on the internet?  (I am using my Mac right now)  How do I get Knetworkmanager back up and running?

---

### Post by GeistDev on 2009-03-19
Please if anyone has any suggestions, I really need some guidance here.

---

### Post by GeistDev on 2009-03-19
Everyone is giving me the ole silent "try to fix it yourself" treatment eh?

OK, well I did try to re-install the network manager by issuing this command:

```
root@chris-desktop:/home/chris# sudo dpkg -i /var/cache/apt/archives/network-manager-kde_1%3a0.2.2-1ubuntu2_i386.deb

```

and I received this messege:

```
 (Reading database ... 130493 files and directories currently installed.)
Preparing to replace network-manager-kde 1:0.2.2-1ubuntu2 (using .../network-manager-kde_1%3a0.2.2-1ubuntu2_i386.deb) ...
Unpacking replacement network-manager-kde ...
dpkg: dependency problems prevent configuration of network-manager-kde:
 network-manager-kde depends on network-manager (>= 0.6.2); however:
  Package network-manager is not installed.
dpkg: error processing network-manager-kde (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 network-manager-kde
```

So that obviously didn't work---why?!

---

