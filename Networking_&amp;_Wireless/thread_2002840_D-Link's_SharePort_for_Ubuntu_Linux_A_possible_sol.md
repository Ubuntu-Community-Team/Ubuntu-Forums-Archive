---
title: "D-Link's SharePort for Ubuntu Linux: A possible solution"
date: 2012-06-13
forum: Networking &amp; Wireless
---

### Post by gamez on 2012-06-13
Hello,

I have been looking around a long time, in this forum and others, to make a printer connected to the USB-Port of my D-Link router DIR-655 work under Ubuntu Linux. Several posts have already requested D-Link's SharePort utility be made available for Ubuntu Linux, but to all what I have heard it remains a closed code Windows-only tool for now.

So what I am proposing here is a solution which works OK for me - but be aware that it is a rather heavy implementation and requires some perceverance to succeed.

It is based on the following idea:
- on your Ubuntu, install a Windows guest using Virtual Box
- install D-Link SharePort (plus the usual printer drivers) into the Windows guest
- Share the printer to the Ubuntu host
- Install the printer within the host

From your Ubuntu host, you are now ready to print to the virtualized printer of the VBox Windows guest.

For your reference, my configuration is the following:
- Kubuntu 12.04 LTS
- Oracle VirtualBox 4.1.16
- Microsoft Windows XP SP3 (as VBox guest) - should also work with Windows 7
- D-Link router DIR-655 - should also work with other models which support SharePort
- D-Link SharePort 1.15 - should also work with the latest version 1.17
- Canon Pixma iP4000 ink-jet printer

How it works:

1) Install the VBox software as usual in your Ubuntu system, and define and install a Windows XP guest OS image as usual; I won't go into further details on this step, I will simply assume that you know what this means and that you have this working for the next steps. Please refer to the Virtual Box documentation and forums for further advise.

2) You may already have noticed that in the default setup, VBox will always configure a single NAT network adapter for the guest, and when you install SharePort in such a (Windows) guest, it won't see your D-Link router. So the first step is to add a second network adapter in the VBox configuration of the guest (or change the configuration of the first adapter accordingly), set its type to "networking bridge", and allow a bi-directional promiscuous mode. I don't exactly know what that means, and if it generates any exposure or risk of intrusion, but at least it has worked for me as such.

3) After you have added the bridge adapter, SharePort (inside the Windows guest) should be able to detect the D-Link router on the network; activate it. When the printer is powered on, the guest should display the usual pop-up that a printer was detected. You can now start to install the related drivers inside the guest, and connect to the printer. Print a test page to make sure that everything is OK between the Windows guest and the printer.
Note: When SharePort connects to the printer, note the related user name (in brackets); it is the name of the Windows VBox "machine", in my case it was "VBOX_WINXP". This user name will be needed later in step 5.

4) Now, we declare the printer as being shared; in the Windows guest, go to "Start" -> "Settings" -> "Printer", locate the printer, click right and select "Share" in the context menu. Enable sharing and give it a name (eg. "iP4000") under which it will be visible to the other network clients. The printer icon changes to include a hand symbol, indicating that the printer is now shared. This is all we need to do on the guest, you can minimize the application window and go back to the Ubuntu world. Of course, if you shut down the guest, or if it hangs up, this procedure won't work anymore either.

5) Now let's go to the Ubuntu system setup to add the new (virtual) printer there. Go to "Printer setup", click "New printer", and then select the connection type "Windows printer via Samba". You get a window which allows you to browse accross all visible Samba shares (in my case, unfortunately, this generated a crash in the SMBBrowser, so I couldn't use this feature), or to enter the smb address directly. Enter the address like in the format <user>/<printer>; in my case it was "vbox_winxp/ip4000". If that works, you are posted to select the maker (canon) and printer type (Pixma iP4000), and it will install the required drivers. If all works fine you'll find a newly defined printer under the given name, with an smb address similar to "smb://vbox_winxp/ip4000". Click on "Print test page" to make a test. When you do so, your print request will become visible in the printer's spool driver within the Windows guest as well.

Note: [In another post]("http://superuser.com/questions/107657/virtualbox-share-guest-windows-xp-printer-to-hostlinux") it is suggested to define some TCP and UDP port forwarding rules in the guest's configuration in order to enable the usage of the guest's printer from the host; in my case no special configuration of the NAT adapter was required after adding a bridge adapter.

In case you dare to try out this procedure, let me know how it goes for you.

Best regards,

g.

---

### Post by buellguy on 2012-12-25
Excellent explanation!

---

### Post by gamez on 2013-02-05
PS:

While Ubuntu seems to install it as a default package, not all Linux distros install the [***smbclient***]("http://packages.ubuntu.com/search?keywords=smbclient") package by default; so if your distro doesn't allow you to browse the network for "Windows printer via Samba" as outlined in **Step 5**, then make sure to install that package beforehand.

Best regards,

g.

---

