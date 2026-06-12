---
title: "Evolution Send/Receive Greyed Out"
date: 2010-08-06
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by drfox on 2010-08-06
Just upgraded to 10.10
Evolution was working fine on Lucid, now my Send/Receive is greyed out. Also, in File> Download messages for offline use, Work online, and Close Window are all greyed out.
What to try?
Larry

---

### Post by lisati on 2010-08-06
Interesting: I would have suggested (un)checking "Work Online" but since that is gryed out too. :(

Possibility: is Evolution under the misapprehension that networking is unavailable?

---

### Post by drfox on 2010-08-06
> **lisati said:**
> Interesting: I would have suggested (un)checking "Work Online" but since that is gryed out too. :(

Possibility: is Evolution under the misapprehension that networking is unavailable?

You got it! I was connected with WICD and Evolution thinks I'm offline. If I connect with NM, Evolution works. Sadly, when I connect with NM I regularly get disconnected every few minutes.
I guess I'll file a bug.
Thanks. 
Larry

---

### Post by drfox on 2010-08-06
I filed a bug on Launchpad, but the developers aren't interested because "Ubuntu ships with Network-Manager."
Crazy. :(
Larry

---

### Post by i386DX on 2010-08-06
So the problem is in fact NetworkManager?
Maybe you should open a bug for that problem (or search if it already exists)

---

### Post by drfox on 2010-08-06
I think the fact that NetworkManager "sucks" is a known issue. :)
I can't use it because I have 2 wireless routers, 1 configured to relay my signal downstairs, and NM gets  confused and keeps disconnecting me. WICD works perfectly. The problem is Evolution: when I'm connect to the net with WICD, everything else works fine; it's just Evolution which thinks I'm offline. When I'm connected with NM, Evo is happy for the 30 seconds or so that I can stay online before NM gets confused and disconnects. 
And Evolution was working fine with WICD in Lucid. It's an Evolution problem--too bad the developer doesn't agree.
Larry

---

### Post by seeker5528 on 2010-08-06
> **drfox said:**
> You got it! I was connected with WICD and Evolution thinks I'm offline. If I connect with NM, Evolution works. Sadly, when I connect with NM I regularly get disconnected every few minutes.
I guess I'll file a bug.

I'm guessing when you installed WICD you did not remove NM.

If you want to keep NM installed then you probably have to do what is listed at [https://answers.launchpad.net/ubuntu/+source/firefox/+question/28829](https://answers.launchpad.net/ubuntu/+source/firefox/+question/28829)

> Open the terminal (Apllication-->accesories--->terminal) and type "sudo gedit /etc/dbus-1/system.d/NetworkManager.conf".
Then you replace the
<allow send_interface="org.freedesktop.NetworkManager"/> with
<deny send_interface="org.freedesktop.NetworkManager"/> (there are three it the text). Then save the changes and reboot. This will not permit firefox (or pidgin) to communicate with network manager and the state will be always online in firefox...

Looks like this file has changed a bit, so it may take a little trial and error to figure out exactly which lines you need to change to deny.

Alternatively you could try installing bum and try using it to disable the network manager service.

To me removing the package 'network-manager' and anything that depends on it seems like the easy solution.

EDIT: You might also be able to rename NetworkManager.conf to something like NetworkManager.disabled to disable the dbus stuff related to network manager.

Later, Seeker

---

### Post by drfox on 2010-08-06
Thanks, Seeker. Back in the day (several releases ago), when I would install WICD, NM would automatically get deleted, and vice-versa. When that stopped happening, I (incorrectly) assumed they could live together in peace and harmony. I've deleted NM, and now Evolution and I are happy again.
BTW, you may want to update your profile. It shows you as an Ibex tester.
Larry

---

### Post by seeker5528 on 2010-08-07
> **drfox said:**
> When that stopped happening, I (incorrectly) assumed they could live together in peace and harmony.

They seem to live together OK, it's just this thing about using dbus to communicate network status that gets in the way. NM does it, WICD doesn't. That's where using bum to set network manager not to start may have been enough, but with things making the transition to upstart there is some question as to the result you will get when using these tools to manage services/daemons to start at boot.

> BTW, you may want to update your profile. It shows you as an Ibex tester.
Larry

That's what I was running when I signed up for the forum and razor blades wasn't an option. ;) OK, changed now.

Later, Seeker

---

