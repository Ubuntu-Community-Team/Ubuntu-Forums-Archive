---
title: "SCP File Transfer not working--hangs after password"
date: 2009-09-15
forum: Networking &amp; Wireless
---

### Post by xcrunner on 2009-09-15
Hi, 
I've been googling for ages but I just can't seem to find the answer to this question.

I want to transfer files across 2 local computers, my desktop and my laptop. SCP seems like the easiest way to do it; so I type in:

scp MYNAME@192.168.1.2:/home/MYNAME/Desktop/TEST .

on my laptop, which should transfer a file from my desktop (192.168.1.2) to my laptop. It goes well, asks for the password. I type it in, and it just hangs. Nothing happens. SSH is working; I can SSH to and from the two computers. But for some reason the SCP won't. 

Any ideas?

---

### Post by uncle-c on 2009-09-16
Do the log files on computer 192.168.1.2 show anything ?

---

### Post by xcrunner on 2009-09-16
> **uncle-c said:**
> Do the log files on computer 192.168.1.2 show anything ?
I'm sorry, I'm kind of a newb and I don't know what that means :(

---

### Post by fela on 2009-09-16
Try scp with the -v option.

This will output more debugging info.

Also, after trying an scp run:

dmesg | tail

on both computers.

---

### Post by xcrunner on 2009-09-16
> **fela said:**
> Try scp with the -v option.

This will output more debugging info.

Also, after trying an scp run:

dmesg | tail

on both computers.
Thanks. I did scp -v (I had actually done it earlier but forgot to mention it). I got a lot of output after I initially did the command; I assume I don't need to print any of it, since it's working up to that point. Then it asks for the password, I type it, and this is the output:

debug1: Next authentication method: password
MYNAME@192.168.1.2's password: 
debug1: Authentication succeeded (password).
debug1: channel 0: new [client-session]
debug1: Entering interactive session.
debug1: Sending environment.
debug1: Sending env LANG = en_US.UTF-8
debug1: Sending command: scp -v -f /home/MYNAME/Desktop/test

I then cntrl-C'd the process since it wasn't going anywhere, and did dmesg | tail

which outputted 

[ 5590.746824] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f4e6cc00
[ 5595.252637] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f4e6cc00
[ 5650.754104] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f4e6cc00
[ 5651.573606] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f4e6cc00
[ 5710.864040] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f4e6cc00
[ 5711.478602] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f4e6cc00
[ 5770.973854] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f4e6cc00
[ 5776.196489] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f4e6cc00
[ 5830.981134] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f4e6cc00
[ 5832.619729] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f4e6cc00


then I went to my Desktop and did the same thing (tried to push a file from my Desktop to my laptop) and got the same error messages, then did dmesg | tail and got this output:

[   59.321352] [drm] Initialized drm 1.1.0 20060810
[   59.324876] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   59.324888] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   59.324969] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   60.980307] NET: Registered protocol family 17
[   74.417920] eth0: no IPv6 routers present
[   80.773755] UDF-fs: No VRS found
[   80.788890] ISO 9660 Extensions: Microsoft Joliet Level 1
[   80.789702] ISOFS: changing to secondary root
[11299.396182] rhythmbox[7104]: segfault at 00000000 eip 00000000 esp b0b0e31c error 4

---

### Post by fela on 2009-09-16
I think the answer is in those messages in the first dmesg...but I might be mistaken.

Try looking into what caused those messages. Also, make sure that the scp *is* hanging!

---

### Post by xcrunner on 2009-09-16
> **fela said:**
> I think the answer is in those messages in the first dmesg...but I might be mistaken.

Try looking into what caused those messages. Also, make sure that the scp *is* hanging!
Thanks. Does anyone have any idea how to figure out what caused them? I'm sorry, I'm pretty new to all this :(

edit- Oh, and I meant to mention--the same problem happens with sftp, i.e., as soon as it asks for the password, I type it in and nothing happens.

---

### Post by fela on 2009-09-16
> **xcrunner said:**
> Thanks. Does anyone have any idea how to figure out what caused them? I'm sorry, I'm pretty new to all this :(

edit- Oh, and I meant to mention--the same problem happens with sftp, i.e., as soon as it asks for the password, I type it in and nothing happens.

I haven't a clue what the messages mean, but the first stop is Google.

I think sftp uses ssh as a backend like scp, so that would explain that (ssh must be the root of the problems). Are you sure ssh works perfectly for just logging on to a command line?

---

### Post by xcrunner on 2009-09-16
> **fela said:**
> I haven't a clue what the messages mean, but the first stop is Google.

I think sftp uses ssh as a backend like scp, so that would explain that (ssh must be the root of the problems). Are you sure ssh works perfectly for just logging on to a command line?
Yep, SSH works perfectly. I can get on my laptop and run commands on my desktop just fine, and vice versa.

---

### Post by xcrunner on 2009-09-17
Oh and I tried one more thing-- 
I SCP'd from each of the two computers to a separate, 3rd party computer.. And it worked for both of them.
So I can SSH from A to B, and I can SSH from B to A.
And I can SCP from A to a third party C, and I can SCP from B to C.

But I can't SCP from A to B

---

### Post by xcrunner on 2009-09-17
Sorry for this extra bump, but one new (really) interesting thing that I've discovered:

There's also something slightly wrong with SSH, and I think this might be the root of the problem but I can't for the life of me figure out why. When I try to SSH from my Desktop to my laptop, it actually doesn't work normally; it says cannot connect to host, port 22, no route to host.

The reason I didn't notice this earlier is because typically I'd notice this, figure something weird was happening, and connect from my laptop to the desktop. This would work. 
Then I'd exit, connect from desktop to laptop, and it would work.

So basically (and I've tested this a few times), I can't just SSH from desktop to laptop. I have to first SSH from laptop to desktop, then exit, and then I can SSH to and from.

Anyway... Sorry for all these posts but this is totally mystifying to me, and I could really use any advice/help anyone has. Thanks!

---

