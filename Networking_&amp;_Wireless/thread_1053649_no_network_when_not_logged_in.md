---
title: "no network when not logged in"
date: 2009-01-28
forum: Networking &amp; Wireless
---

### Post by giorgio.p on 2009-01-28
I have set up a computer using Intrepid Ibex.
I have got port forwarding working.
I have got apache running.
I can ssh to the box from anywhere.....

HOWEVER.
As soon as I log out of the computer or reboot it, I can no longer do anything. ie the network does not appear to connect until I physically log in locally on the box.

I have done the same setup before with Feisty with no problems at all.

Can anybody point me in the right direction as it is unusable like this. I intend to run the computer headless in a cupboard.

Cheers
George

---

### Post by Sam Lars on 2009-01-29
Are you using Network Manager to connect?  You have to log in for this to work.  If you go to your network connection settings, you can manually set up your connections.  This should work without making you log in.

---

### Post by giorgio.p on 2009-01-30
Thanks for the reply.
I tried disabling NetworkManager with an update-rc.d remove etc but it still didnt work.

I then did an "apt-get remove network-manager gnome-network-manager" and it now works fine.

Thanks again
George

---

