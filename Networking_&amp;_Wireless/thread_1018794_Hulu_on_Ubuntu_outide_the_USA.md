---
title: "Hulu on Ubuntu outide the USA"
date: 2008-12-22
forum: Networking &amp; Wireless
---

### Post by corman420 on 2008-12-22
Hello all,

I've been trying to get OpenVPN to work with Ubuntu 8.10, but the guide I'm using doesn't seem to be up-to-date.

[http://www.ventanazul.com/webzine/articles/openvpn-ubuntu-and-hulu](http://www.ventanazul.com/webzine/articles/openvpn-ubuntu-and-hulu)

Basically, I'm in Canada and I would like to use the Hulu service. I used to use OpenVPN on Windows, and it worked (sometimes).

Now I would like to use it on my Ubuntu machine. using the guide above, I get to the point where I source /vars. And then I get stuck.

FYI: I've copied directory 2.0 to /easy-rsa. 

But when I try to run . ./vars (or source /vars as stated in the comments), I get an error stating it cannot find a file, or I get this:

[I]Please edit the vars script to reflect your configuration,
then source it with "source ./vars".
Next, to start with a fresh PKI configuration and to delete any previous certificates and keys, run "./clean-all".
Finally, you can run this tool (pkitool) to build certificates/keys.[/I]

Perhaps, using OpenVPN for this sort of thing is outdated. 

If anyone has any suggestions as to anything else to use, or provide some help to install OpenVPN, that would be great!

By the way, I tried using proxies, doesn't work for Hulu. Also tried TOR with the plugin for Firefox, that doesn't work either.

---

### Post by BoGs on 2009-04-14
I just setup a server for me and my friends to access the wonders and benefits of the us market without having to livein the us ex hulu.

First (you didnt mention it) but you need to have some sort of server dedicated or vps within a datacenter in the us with root access.

Do you still have a problem with this issues as the thread is old, I can probably help more if I know you still have issues.

---

### Post by sdm_cacto on 2009-04-14
OK, im looking for the same as you. In windows XP i can use Hotspot shield, is super simple, is there something like that for Ubuntu? I dont understand OpenVPN but it seems like it is the tool we are looking for.

---

### Post by orduek on 2010-01-19
same here. any replacement for hotspot?

---

### Post by ApEkV2 on 2010-01-19
You could try a combination of Privoxy and Tor.
Although the tor circuits have been getting slower (not enough ppl sharing bandwidth).

---

### Post by orduek on 2010-01-23
> **Cabling said:**
> Did that work? :)

nope :(

---

