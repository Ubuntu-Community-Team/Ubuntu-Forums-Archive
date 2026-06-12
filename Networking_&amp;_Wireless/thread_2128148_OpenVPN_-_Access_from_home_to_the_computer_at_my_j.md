---
title: "OpenVPN - Access from home to the computer at my job's office"
date: 2013-03-22
forum: Networking &amp; Wireless
---

### Post by damog88 on 2013-03-22
Hi everyone!

I'm kinda new in this whole Ubuntu business...and now I'm trying to connect via openvpn to the net of my working place. I was given a username and an access key, and also two files: one of configuration, and another was a certificate.

But when I write down the following command: "sudo openvpn --config path/ofconfig/file --ca /path/ofcertif/file"

I am asked for my user/pass, and then it runs, but it gets stuck where it says: "day mth XX HH:MM:SS YYYY Initialization Sequence Completed"

And it won't let me write anything unless I finish the process by hitting Ctrl+C.

I don't really know wether it doesn't connect, or if I'm doing something wrong... The thing is that I need access to the machine in my working place, and I'd like to do it through the console, so I'll be thankful if anyone would be able to help.

Thank you very much!

Cheers!

---

### Post by iponeverything on 2013-03-22
silly question, but are you literally using this command?  

> sudo openvpn --config path/ofconfig/file --ca /path/ofcertif/file

---

### Post by damog88 on 2013-03-22
> **iponeverything said:**
> silly question, but are you literally using this command?

No... I put in there the path to the config. and the certificate files...

Besides that... I said that the program asks me for my user and pass, and then it begins to run, and if I was "literally" using that command...I think it won't be asking me anything...

---

### Post by SeijiSensei on 2013-03-22
The standard method for using openvpn is to place the configuration file and any keys or certificates in /etc/openvpn and enable the openvpn "daemon" to run at boot.  If the configuration includes the "remote" directive, the daemon will start trying to set up a session with the remote server as soon as the network is available.

I recommend dropping by the OpenVPN site, [http://openvpn.net/](http://openvpn.net/), and browsing the documentation there.  There is also a specific [Ubuntu document for OpenVPN]("https://help.ubuntu.com/community/OpenVPN").

---

