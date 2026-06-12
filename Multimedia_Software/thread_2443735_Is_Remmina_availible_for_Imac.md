---
title: "Is Remmina availible for Imac?"
date: 2020-05-19
forum: Multimedia Software
---

### Post by aughey on 2020-05-19
I started playing about with Remmina. Once I figured out how to switch on sharing permissions then entering IP address it just worked between my two Ubuntu computers. I would like to be able to do this with an Imac. There was an online item from a guy who said he was  reconfiguring remmina to work on a mac. I would not have a clue where to start. Is there a ready to go imac version will allow me to remotely access the Imac. Also will it allow file sharing. Thanks guys

---

### Post by DuckHook on 2020-05-19
Please be very very careful using Remmina. All of these VNC/RDP-type apps are frighteningly insecure in their default configurations. They should only be used within a properly firewalled local LAN. If venturing outside into the big bad world, the only way I would feel comfortable using them would be if they were tunneled through a SSH connection.

Instructions:
[https://remmina.org/remmina-rdp-ssh-tunnel/](https://remmina.org/remmina-rdp-ssh-tunnel/)
[https://www.linuxliteos.com/forums/tutorials/tutorialll-3-0-remote-desktopremminassh-tunnelkeyson-other-linux-osad-hoc/](https://www.linuxliteos.com/forums/tutorials/tutorialll-3-0-remote-desktopremminassh-tunnelkeyson-other-linux-osad-hoc/)

Please note that I can be of only limited help here. I don't use VNC/RDP-type apps because they are so insecure, so my knowledge is limited.

As to your question:

Remmina is a Linux App. No native version exists for non-Linux OSes. However, being open source, I suppose some enterprising soul is always at liberty to compile it for another OS. However, it relies on GTK libraries, so such a port would not be a trivial exercise.

If you want to remote desktop with other OSes, I would suggest other VNC clients that are cross-platform. They all suffer from the security flaws that I mention above and can only be safely used through some sort of encrypted tunnel.

---

### Post by DuckHook on 2020-05-19
There is also this: [https://askubuntu.com/questions/1110648/remmina-unable-to-establish-connection-to-rdp-server-to-macbook](https://askubuntu.com/questions/1110648/remmina-unable-to-establish-connection-to-rdp-server-to-macbook)

---

### Post by TheFu on 2020-05-19
Going from a Mac to most Linux systems with a remote desktop using **x2go** is pretty easy. x2go is an NX protocol implementation.
Going either from Mac to Linux or Linux to Mac using **ssh** is pretty easy.
I have no clue how to get from anything to a Mac with a GUI, which is the question you are asking. Apple has a proprietary GUI and has sued people for trying to have the same look and feel.

Linux supports standard protocols and tends to use the names for those protocols.

Apple *sometimes* supports the standard protocols, but seems to Applify-the names used for some reason. I think it is there attempt to confuse me, personally. ;)

---

