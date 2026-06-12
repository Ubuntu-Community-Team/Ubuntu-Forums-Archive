---
title: "Remuco, k800i and Amarok"
date: 2007-05-16
forum: Multimedia &amp; Video
---

### Post by toasterofirony on 2007-05-16
Why can't they be friends?

But seriously, I have the 0.5.1 client on my k800i and the remuco-server-amarok_0.4.3.1-0ubuntu2feisty_i386 server installed. Everytime I run the server and try and connect with the client it says "connection failed" and fails to give me any information why. I can connect my PC to my 'phone with Nautilus to send files via BT and I have an HID controller on my 'phone I can connect to, but Remuco doesn't want to play ball. Is it possible that the 'phone doesn't have permission to connect to the server?

My /etc/bluetooth/hcid.conf for what it's worth:

```
#
# HCI daemon configuration file.
#

# HCId options
options {
	# Automatically initialize new devices
	autoinit yes;

	# Security Manager mode
	#   none - Security manager disabled
	#   auto - Use local PIN for incoming connections
	#   user - Always ask user for a PIN
	#
	security user;

	# Pairing mode
	#   none  - Pairing disabled
	#   multi - Allow pairing with already paired devices
	#   once  - Pair once and deny successive attempts
	pairing multi;

	# Default PIN code for incoming connections
	passkey "1234";
}

# Default settings for HCI devices
device {
	# Local device name
	#   %d - device id
	#   %h - host name
	name "%h-%d";

	# Local device class
	class 0x3e0100;

	# Default packet type
	#pkt_type DH1,DM1,HV1;

	# Inquiry and Page scan
	iscan enable; pscan enable;
	discovto 0;

	# Default link mode
	#   none   - no specific policy 
	#   accept - always accept incoming connections
	#   master - become master on incoming connections,
	#            deny role switch on outgoing connections
	lm accept;

	# Default link policy
	#   none    - no specific policy
	#   rswitch - allow role switch
	#   hold    - allow hold mode
	#   sniff   - allow sniff mode
	#   park    - allow park mode
	lp rswitch,hold,sniff,park;
}
```

Can someone please tell me what I'm doing wrong?

---

### Post by toasterofirony on 2007-05-17
~bump~

I know it's terribly bad form, but I'm sure that someone will take pity on me and have an idea what I'm doing wrong.

Anyone?

---

### Post by masala on 2007-05-18
Since Remuco works on a SE k750i, M600i and W850i, I guess it is not a software bug, but a permission issue. The hcid.conf file looks good, so the permission issue may be locted on the mobile.

There is a similar problem in discussion in the Remuco mailing list: [http://sourceforge.net/mailarchive/forum.php?thread_name=5b96821e0705171355p4b0fe655ua7c639d15bcbb368%40mail.gmail.com&forum_name=remuco-main](http://sourceforge.net/mailarchive/forum.php?thread_name=5b96821e0705171355p4b0fe655ua7c639d15bcbb368%40mail.gmail.com&forum_name=remuco-main). Maybe the thread helps in your situation !?

---

### Post by toasterofirony on 2007-05-19
Thanks, but it seems to have resolved itself as of this morning, which is pretty bizarre. Something I've got used to in Linux :P

That said, I think the amarok server has got a serious memory leak, as everytime I run it the usage of my physical memory rockets up.

---

### Post by masala on 2007-05-19
> **toasterofirony said:**
> That said, I think the amarok server has got a serious memory leak, as everytime I run it the usage of my physical memory rockets up.

Yep, that's true :( .
Remuco is currently under heavy development to get extended by some more groovy features. While doing so, the server has been almost completely rewritten - this time strictly observing potential memory leaks. So the next release (which is probably in ~2 month) should solve the memory leak problem.

---

