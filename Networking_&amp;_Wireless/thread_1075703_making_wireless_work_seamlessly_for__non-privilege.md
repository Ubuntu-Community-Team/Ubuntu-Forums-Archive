---
title: "making wireless work seamlessly for  non-privileged user"
date: 2009-02-20
forum: Networking &amp; Wireless
---

### Post by xurizaemon on 2009-02-20
I am installing an Ubuntu 8.10 machine for a family, and by default want it to boot up to an unprivileged account for their son to use.

When I log into Gnome using the account created during install (admin account), nm-applet fires up and the wireless connection works fine.

If I set the machine to boot by default into the non-privileged account, however, then the wireless connection isn't established (and nm-applet doesn't start).

How can I configure it to do so? I had hoped that granting the user permission "Connect to wireless and ethernet networks" in the Users admin panel would do this. The user is correctly added to the netdev group, but still doesn't appear to get networking going.

After installation, I didn't find I had to do any extra configuration to get wireless working under the admin account; nm-applet detected the USB wireless stick (works fine with either a D-Link GW122 rC1, or a Netgear WG111v3), and prompted for a password to join the network when I clicked on the nm-applet icon.

So, I'm not sure what steps to take to get the same functionality under the less privileged account!

The reason I want to run it on a non-privileged account per default is that the primary user will be an autistic teenager, and the family have had some issues with the previous (Windows OS) install getting a bit messed up :)

Thanks in advance!

---

### Post by xurizaemon on 2009-02-21
I'd still like to hear what the correct setup method is :)

I'd only just installed, so I decided to try an experiment, and it seemed to work. What I did was:

```
cd ~privilegeduser
tar -cf - . | ( cd ~unprivilegeduser ; sudo tar -xvf - ) 
sudo chown -R unprivilegeduser: ~unprivilegeduser
```

reboot

log in as unprivilegeduser

```
rm -rf .gnome2/keyrings
```

done.

---

