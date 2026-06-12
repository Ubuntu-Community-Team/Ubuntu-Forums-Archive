---
title: "Remote control of Windows Computer"
date: 2011-04-11
forum: Networking &amp; Wireless
---

### Post by wabbit46 on 2011-04-11
I have a very simple network of two computers. One is running ubuntu (Maverick) and the other running Windows (Vista).

The two computers are networked satisfactorily but I wish to control the Vista computer from the ubuntu one.

I have tried running UltraVNC on the Vista computer and the default VNC from ubuntu. 

However neither computer can see the other using VNC.

Can anyone assist in how I can control the Vista machine remotely?

---

### Post by Grenage on 2011-04-11
Doesn't Windows Remote Desktop offer this natively?  Failing that, there is a freenx client for Windows.

---

### Post by wabbit46 on 2011-04-11
> **Grenage said:**
> Doesn't Windows Remote Desktop offer this natively?  Failing that, there is a freenx client for Windows.

Thanks for your help Grenage. The Vista system does not appear to connect to a VNC client. To use freenx I think I would have to load it on both computers.

---

### Post by Grenage on 2011-04-11
> **wabbit46 said:**
> Thanks for your help Grenage. The Vista system does not appear to connect to a VNC client. To use freenx I think I would have to load it on both computers.

What I mean is, can't you use Vista's native RDP support?  Under *internet* in your application menu, you should have *Terminal Server Client*; can you not connect to the Vista machine using that?  If not, perhaps it's not enabled on the Vista machine - I 'think' it's under system properties.

---

### Post by wabbit46 on 2011-04-12
> **Grenage said:**
> What I mean is, can't you use Vista's native RDP support?  Under *internet* in your application menu, you should have *Terminal Server Client*; can you not connect to the Vista machine using that?  If not, perhaps it's not enabled on the Vista machine - I 'think' it's under system properties.

Thanks again Grenage. The Vista RDP is enabled but the ubuntu computer cannot see it.

---

### Post by Grenage on 2011-04-12
> **wabbit46 said:**
> Thanks again Grenage. The Vista RDP is enabled but the ubuntu computer cannot see it.

I'd be lying if I said that Linux's RDP didn't have some issues with the more modern MS implementations, but I was sure it worked ok with Vista.  Where you enable RDP on the Vista machine, is there an option to allow connections from *any* version of RDP?

---

### Post by cpkirk on 2011-04-12
make sure you open the appropriate ports in both machines firewalls...that can be why the ubuntu machine can't see the vista one. note that vista has a built in firewall that is enabled by default.

---

### Post by wabbit46 on 2011-04-12
> **cpkirk said:**
> make sure you open the appropriate ports in both machines firewalls...that can be why the ubuntu machine can't see the vista one. note that vista has a built in firewall that is enabled by default.

Thanks for your advice cpkirk, I have already disabled the Vista firewall and I do not think I have have one on the ubuntu computer.
Should I remove VNC from the ubuntu computer?

---

### Post by wabbit46 on 2011-04-25
For any who is interested.

I have finally solved it.

On the Vista PC I have tightVNC Server installed. This program automatically modifies the Windows Firewall to allow traffic to pass. I have been able to re-enable the Windows Firewall.

On the ubuntu PC you need to run Vinagre Remote Desktop Viewer (v2.30.2 in my case).

The Vista computer is not visable using a search from Vinagre, However typing in its IP address allows the connection to proceed.

I am unsure how this solution would work when the IP addesses are dynamically allocated

---

