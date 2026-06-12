---
title: "Can't disable ipv6"
date: 2005-03-10
forum: Networking &amp; Wireless
---

### Post by Swab on 2005-03-10
So I uncommented:
alias net-pf-10 off           # IPv6

Then I updated my modules, but still lsmod shows ipv6, even after reboot, and ifconfig shows i have an ipv6 address... what to do?

---

### Post by bored2k on 2005-03-10
[QUOTE=Swab]So I uncommented:
alias net-pf-10 off           # IPv6

Then I updated my modules, but still lsmod shows ipv6, even after reboot, and ifconfig shows i have an ipv6 address... what to do?[/QUOTE]
 Try this other method
in firefox address> about:config
find networking_disable_ipv6 change false to true.

---

### Post by Swab on 2005-03-10
[QUOTE=bored2k]Try this other method
in firefox address> about:config
find networking_disable_ipv6 change false to true.[/QUOTE]

Thanks for the reply, I already have ipv6 disabled in firefox, but it's taking forever to resolve host names.

---

### Post by bored2k on 2005-03-10
[QUOTE=Swab]Thanks for the reply, I already have ipv6 disabled in firefox, but it's taking forever to resolve host names.[/QUOTE]

Try this :
 [QUOTE=Monika]This didn't work for me. But I looked around the forums and there's two other things I did and all three of them together seem to bring the desired effect

editing /etc/modprobe.d/aliases
1. open /etc/modprobe.d/aliases in a text editor with root privilages (for example write 'sudo gedit /etc/modprobe.d/aliases' into a terminal)
2. edit line:
> 
alias net-pf-10 ipv6

to
Code:

alias net-pf-10 off

[/QUOTE]

---

### Post by Swab on 2005-03-10
[QUOTE=bored2k]Try this :[/QUOTE]

Yeah, thats what  i did already, is there something else I need to do?  That post says there are 3 things.

---

### Post by Swab on 2005-03-10
Actually, it seems like my ISP just have crappy DNS servers.. I tried some others and its much faster.

---

### Post by bored2k on 2005-03-10
[QUOTE=Swab]Actually, it seems like my ISP just have crappy DNS servers.. I tried some others and its much faster.[/QUOTE]
 If the above don't work, we need an expert help because I already gave all 3 options I know [yours, firefox's, and the last one].

---

### Post by Swab on 2005-03-10
[QUOTE=bored2k]If the above don't work, we need an expert help because I already gave all 3 options I know [yours, firefox's, and the last one].[/QUOTE]

Yeah, I spoke too soon, even using alternate DNS servers isn't helping.  I've only tried 2 options, the last one and mine were the same thing.

---

### Post by bored2k on 2005-03-10
[QUOTE=Swab]Yeah, I spoke too soon, even using alternate DNS servers isn't helping.  I've only tried 2 options, the last one and mine were the same thing.[/QUOTE]
 I'm sure there are 3 methods, search ipv6 here, you will find it .
I know its in the Starters HowTo sticky tho.

---

### Post by Swab on 2005-03-11
OK, this disabled ipv6 for me:

Created a /etc/modprobe.conf file with the following lines:
alias net-pf-10 off
alias ipv6 off

Now I do not have ipv6 module loaded!  Hosts seem to resolve much faster now.

---

### Post by bored2k on 2005-03-11
[QUOTE=Swab]OK, this disabled ipv6 for me:

Created a /etc/modprobe.conf file with the following lines:
alias net-pf-10 off
alias ipv6 off

Now I do not have ipv6 module loaded!  Hosts seem to resolve much faster now.[/QUOTE]
 Awsome, imma send this right to my personal FAQ (I have/update my personal version of the unofficial ubuntu guide, with the stuff I need, bugs I see getting solved, etc ;)).

---

### Post by Swab on 2005-03-11
[QUOTE=bored2k]Awsome, imma send this right to my personal FAQ (I have/update my personal version of the unofficial ubuntu guide, with the stuff I need, bugs I see getting solved, etc ;)).[/QUOTE]

Yeah, it's a great idea to keep a log of all these things!

---

### Post by ardvark on 2005-03-19
I had a problem with doing this last fix. While it did help to speed up internet access, it also stopped my SOUND CARD  and Floppy drive from being recognized. So I had to to remove it. Does anyone know why this happened?

---

### Post by Swab on 2005-04-08
[QUOTE=ardvark]I had a problem with doing this last fix. While it did help to speed up internet access, it also stopped my SOUND CARD  and Floppy drive from being recognized. So I had to to remove it. Does anyone know why this happened?[/QUOTE]

Yes, when you edit the modprobe.conf file add a line that reads:

include /etc/modprobe.d/

This should solve the problem.

---

### Post by arctic on 2005-04-08
[QUOTE=Swab]Yeah, it's a great idea to keep a log of all these things![/QUOTE]
there is already a howto in the 4.10 network section for this topic. you guys should start to learn how to use forums and search tools ;)

---

### Post by nautilus on 2005-04-14
...don't disable ipv6  [-X 

and no, resolving isn't any faster at all unless you have (had) a default route set for ipv6 somehow

look at how resolving works:

ask hosts as domain prefix...
ask hosts as is..
ask dns as domain prefix...
ask dns as is...

and in all these cases, we are simply asking for two records, recursively, an AAAA and an A

it'll ask for both, anyway, with or without an ipv6 kernel module, due to it being a C implementation, not a kernel implementation.

next point; asking for the AAAA is about as intensive as asking for a CNAME... big deal.

stay away from those next generation protocols, they'll "slow you down"   ](*,)

alright, honestly, i love ubuntu BECAUSE of it's ipv6 out-of-the-box.

i think it's the first distro i've ever used which supported the current internet standard protocol, without tweaking, recompiling, or installing other rubbish.

so i come here and see you guys... taking it out?!

for shame!   :grin:

---

### Post by arctic on 2005-04-15
> **nautilus]...don't disable ipv6  [-X 

and no, resolving isn't any faster at all unless you have (had) a default route set for ipv6 somehow

look at how resolving works:

ask hosts as domain prefix...
ask hosts as is..
ask dns as domain prefix...
ask dns as is...

and in all these cases, we are simply asking for two records, recursively, an AAAA and an A

it'll ask for both, anyway, with or without an ipv6 kernel module, due to it being a C implementation, not a kernel implementation.

next point said:**
> (*,)

alright, honestly, i love ubuntu BECAUSE of it's ipv6 out-of-the-box.

i think it's the first distro i've ever used which supported the current internet standard protocol, without tweaking, recompiling, or installing other rubbish.

so i come here and see you guys... taking it out?!

for shame!   :grin:
 actually, a lot of distros work with ipv6 out of the box. fedora does, mandrake does, yoper does, kanotix does, mepis does etc....
you should keep in mind that certain stuff that works for you does not work for the rest of the users. most routers do have serious trouble with ipv6, declining ANY web-browsing. so disabling it is sometimes the only chance in order to surf the web, send mails and download system updates. anyway... once you have disabled it, you can always re-enable it with a few hacks to your scripts. so i do not really understand your concerns.

---

### Post by nautilus on 2005-04-15
how can a router break because a host has ipv6 support?

there's a difference between having the support for it in the kernel, and actually using it.

it wouldn't shock me terribly if half the ubuntu users have appletalk support in their kernel also, but again, i highly doubt this breaks their networking.

as for distros, i didn't really know that.  in fact, i've only used about 4 in my lifetime, and Debian has consumed most of that time.

but a router which breaks because a host has ipv6 support ... that's a tough pill to swallow.

---

