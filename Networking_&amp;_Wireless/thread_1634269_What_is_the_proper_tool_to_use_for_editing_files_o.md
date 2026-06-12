---
title: "What is the proper tool to use for editing files on a server?"
date: 2010-11-30
forum: Networking &amp; Wireless
---

### Post by anthony62490 on 2010-11-30
I have a gaming server set up and running client software 24/7. This prevents me from editing the configuration files while the client is running. The server is connected to a switch which also connects another computer to the internet.

What would be the proper software to use if I want to edit files on the server without interrupting the client?

I have looked at Samba, SSH, and Screen, but I'm not entirely sure which one would be the best tool for the job.

Any ideas?

---

### Post by chili555 on 2010-11-30
I'd suggest logging in to the server with ssh. If you have a static IP for the server, and you should:```
ssh -l user 192.168.blah.blah
```Then I'd use vim:```
sudo vim /etc/config/file
```After you have saved and closed the file, you'll need to restart any services dependent on the file:```
sudo service example restart
```Then log out of ssh and you're done.

---

### Post by Boondoklife on 2010-11-30
On an additional note, unless the server software scans the config files for changes on its own, and is capable of implementing the changes without interrupting client/server IO; The server will have to be gamer free for the service to be restarted as chili said. If not you will disconnect the gamers when you restart it.

With this in mind, don't expect it to be an uninterrupted event.

---

### Post by anthony62490 on 2010-12-01
Okay, SSH is proving to be a bit of a headache to set up, but I should understand it after a bit more searching.

In the meantime, I have installed Screen. It does exactly what I need it to do. I can edit files while the game runs in the background and then reload the files all without stopping the client. The only drawback is that I have to have the keyboard plugged into the server.

Thanks for the help.

---

### Post by Boondoklife on 2010-12-01
Your only real options are ssh or it's stupid older brother telnet. I would not recommend telnet unless it is on a local network usage as information is sent with out encryption.

---

### Post by pricetech on 2010-12-01
> **Boondoklife said:**
> stupid older brother telnet.

Not stupid, just naive.

SSH to the server is your best option.

I like nano as a command line text editor.  Plain vanilla, which is what I want in a text editor.

---

### Post by Boondoklife on 2010-12-01
Nah stupid fits better, I mean anyone that writes sensitive information in plain text on a medium is just stupid! Seriously I don't think there is a person alive that doesn't realize this fallacy in some capacity.

---

