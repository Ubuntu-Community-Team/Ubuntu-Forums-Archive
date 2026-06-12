---
title: "Setting up static IP"
date: 2009-10-25
forum: Networking &amp; Wireless
---

### Post by sideburns on 2009-10-25
I'm trying to set up my sister's Ubuntu box so that she can ftp into it (via ssh) from her laptop.  I know how to configure the router, but I need to set her up on static IP and can't find the appropriate tool.  I know how to do it on Fedora, but the tools I need don't seem to be there on Ubuntu.  If there is a standard tool installed, what is it; if not, what do I need to install?  Thanx!

---

### Post by ibutho on 2009-10-25
The file you need to edit is /etc/network/interfaces. More details on setting up static IPs are [here]("http://www.techiecorner.com/486/how-to-setup-static-ip-in-debian/").

---

### Post by sideburns on 2009-10-25
Thank you.  I'm vastly amused both by the fact that Ubuntu, of all distros, has no way to do this via GUI, and that whoever wrote that article expects Ubuntu users to know an arcane, obsolete, line editor like vi.  However, I know how to get a proper editor like nano onto her box and can do the work.  Again, thanx for the pointer.

Almost forgot: there doesn't seem to be anything there about DNS.  Does that go in the same file or what?

---

### Post by sideburns on 2009-10-25
A little googlemancy found the answer: [http://www.nalinmakar.com/2008/11/08/static-ip-address-on-ubuntu-810/](http://www.nalinmakar.com/2008/11/08/static-ip-address-on-ubuntu-810/) not only shows how to set up static IP, it shows where to put the nameservers as well.

---

### Post by Iowan on 2009-10-25
Ubuntu comes with **nano** and **gedit**.  You *should* be able to set up a manual (static) address via Network Manager itself.  Depending on your DHCP server, it might also be possible to use it to issue a static lease based on MAC address - and leave the machine set up for DHCP.

---

### Post by sideburns on 2009-10-25
Yeah; I found out about nano when I tried to install it.  (Not a problem; I'd rather find out that it's already installed than try to use it when it's not.)  I've got the static set up now, no problem.  Alas, I'm having trouble with ssh, but that's a different thread.

---

### Post by ibutho on 2009-10-26
> **sideburns said:**
> Thank you.  I'm vastly amused both by the fact that Ubuntu, of all distros, has no way to do this via GUI, and that whoever wrote that article expects Ubuntu users to know an arcane, obsolete, line editor like vi.  However, I know how to get a proper editor like nano onto her box and can do the work.  Again, thanx for the pointer.

Almost forgot: there doesn't seem to be anything there about DNS.  Does that go in the same file or what?

The article I posted is actually for Debian and thats probably why the editor used was vi. DNS servers are configured in /etc/resolv.conf. As for Ubuntu lacking a decent GUI for network config, I too am surprised by this. Ubuntu lacks many GUI sysadmin tools which means that some things can only be done in the CLI unlike say Fedora, openSUSE or Mandriva where you can use the CLI or a GUI interface. I don't mind using the CLI, but for a distro that claims to be user friendly they certainly aren't making it any easier for newbies.

---

### Post by chili555 on 2009-10-26
> As for Ubuntu lacking a decent GUI for network configYou most certainly can set up a static IP with a GUI in Ubuntu. Right click Network Manager and Edit Connections and set it up in the attached.

---

### Post by ibutho on 2009-10-27
> **chili555 said:**
> You most certainly can set up a static IP with a GUI in Ubuntu. Right click Network Manager and Edit Connections and set it up in the attached.

Interesting. I never knew that existed.

---

