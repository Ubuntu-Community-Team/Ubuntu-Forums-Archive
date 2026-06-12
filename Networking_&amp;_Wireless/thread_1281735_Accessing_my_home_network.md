---
title: "Accessing my home network"
date: 2009-10-03
forum: Networking &amp; Wireless
---

### Post by mrkazoodle on 2009-10-03
Hi

When I try to access my home network (Locations > Network > Windows-network) I get a window which asks for a password, but none of my windows machines have passwords, and my ubuntu password doesn't work.
And on my windows machines I don't ever need a password to acces my network.
Strangely I remeber being able to access my networkdrive when my vista laptop was running.

I'm able to access my network drive by mounting it (/etc/fstab), so that problem is partially fixed
(but I can't open it by browsing locations > network!!!!!)
But to get my network printer to work (system > 'Beheer' (dutch) > printing) I get the same password window as when I try to open my windows-network
I need a way around that password problem, becaus here I get the same window as when I try opening my windows-network.

I have already searched for a solution, but I couldn't find it, I hope you guys can help me out.

---

### Post by LeslieL on 2009-10-03
I have exactly the same problem - you've expressed it very well. Anyone know what's going on?

---

### Post by lolium on 2009-10-03
I am not sure if this will help you out but maybe, set a password for the administrator account on windows, and then use that password. Not sure if it will work just an option to try.

---

### Post by mrkazoodle on 2009-10-04
> **lolium said:**
> I am not sure if this will help you out but maybe, set a password for the administrator account on windows, and then use that password. Not sure if it will work just an option to try.

Thanks, but this won't help, the problem is not password related, my windows machines can access the network and they don't ask for passwords, not even when one of them has a password protected account.

I 've got an idea about being able to 'open' my windows-network when my vista machine is running: I think it has created a new network, one I did manage to 'open', I'm going to try to do this again.

cya

---

### Post by mrkazoodle on 2009-10-10
Hi,

I've tested it and when my vista machine is running,
And I was able to access my windows-network!
I think it's because Vista has made a new workgroup because it is a dutch version and it called it "werkgroep", so this new workgroup is accessable for ubuntu.
So I guess that if I'd be able to get my other computers to stop 'running' the old workgroup and get them to use nothing else but the vista one I might be able to access my network drive easily

greets

---

### Post by ST3ALTHPSYCH0 on 2009-10-19
I just cleared up an identical problem that included not being able to print to my windows printer. I had to uninstall Windows Live Assistant. Give it a try.

---

### Post by LeslieL on 2009-10-19
I don't have Windows installed on my machine, and the part of the network I'm most interested in is our shared storage drive. But a recent update seems to have eliminated the problem most of the time. Not all the time though! Aren't computers wonderful!

---

### Post by ST3ALTHPSYCH0 on 2009-10-19
don't ya love those intermittent problems? They're especially great when you're a service tech.... people just love to be told that if it doesn't happen for you that you can't troubleshoot it!

---

### Post by mrkazoodle on 2009-10-25
Hi,

The problem is solved, I started every windows computer and changed their workgroup names to WERKGROEP, hereby deleting the old workgoup
(or whatever it's called, you can find it in the (right-click) My Computer > properties)

note: I also had my NAS running, I don't know if this makes a difference

---

