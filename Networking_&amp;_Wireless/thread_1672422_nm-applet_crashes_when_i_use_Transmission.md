---
title: "nm-applet crashes when i use Transmission"
date: 2011-01-20
forum: Networking &amp; Wireless
---

### Post by elidoperezmd on 2011-01-20
Hi all, thanks for reading.

Every time i open Transmission the nm-applet crashes, like 10 minutes after opening it. It has been like that for i don't know how long. I don't wanna have another client. So, have anyone heard of this before, or a solution for this?

every help will be appreciated, thanks

---

### Post by argued.logic on 2011-01-21
So there are 2 of us having issues with nm-applet then. Strange, I would think more are but having said that, I did not get any responses in my thread.

What you could try is open up an terminal and type "killall nm-applet".
Once all instances are closed fire it up by "sudo nm-applet --sm-disable" and
see if that gives you stability as it did for me, the mem-leak issue is still there 
for me tho. Let me know how it turned up and lets hope we get some help from
others with similar issues as well.

---

### Post by elidoperezmd on 2011-01-22
> **argued.logic said:**
> So there are 2 of us having issues with nm-applet then. Strange, I would think more are but having said that, I did not get any responses in my thread.

What you could try is open up an terminal and type "killall nm-applet".
Once all instances are closed fire it up by "sudo nm-applet --sm-disable" and
see if that gives you stability as it did for me, the mem-leak issue is still there 
for me tho. Let me know how it turned up and lets hope we get some help from
others with similar issues as well.

HI, thanks for your help, i have to say that after trying your sugestion, i could use the transmission for about 3 hours, straight, but after a while nm-applet crashed again.

I still looking for a definitive fix. Thanks for your time and help.

---

### Post by argued.logic on 2011-01-22
> **elidoperezmd said:**
> HI, thanks for your help, i have to say that after trying your sugestion, i could use the transmission for about 3 hours, straight, but after a while nm-applet crashed again.

I still looking for a definitive fix. Thanks for your time and help.

For every problem there is a solution. What is the version of your network-manager and
nm-applet? Also take your time and read through my other thread of nm-applet problems
and maybe you ll find the answer there since it solved all my problems.

---

### Post by elidoperezmd on 2011-01-22
> **argued.logic said:**
> For every problem there is a solution. What is the version of your network-manager and
nm-applet? Also take your time and read through my other thread of nm-applet problems
and maybe you ll find the answer there since it solved all my problems.

OK, ill read you other post to see if there is anything that helps, i just realized that your advice worked, but after a restart or even going into stand by, if i connect to transmission again it will do the same thing again....how do i get the version of the network manager and nm-applet.

Dude, you cant imagine of how much help you are being

---

### Post by argued.logic on 2011-01-23
> **elidoperezmd said:**
> OK, ill read you other post to see if there is anything that helps, i just realized that your advice worked, but after a restart or even going into stand by, if i connect to transmission again it will do the same thing again....how do i get the version of the network manager and nm-applet.

Dude, you cant imagine of how much help you are being

I am glad to help - thats all we are here for.
You should be able to open up synaptic package manager and look for network-manager-gnome and see what version you have installed. Also right-click on your
nm-applet and choose About will give you the version. This is the easy way.
Something that comes to my mind regarding your problem is a question - How does
the nm-applet crash and effect your connection since it really shouldn't, it is only a GUI
frontend to network manager. Answer those questions and we should be able figure it 
out.

P:s do you have elementary-art ppa active?

---

### Post by elidoperezmd on 2011-01-23
> **argued.logic said:**
> I am glad to help - thats all we are here for.
You should be able to open up synaptic package manager and look for network-manager-gnome and see what version you have installed. Also right-click on your
nm-applet and choose About will give you the version. This is the easy way.
Something that comes to my mind regarding your problem is a question - How does
the nm-applet crash and effect your connection since it really shouldn't, it is only a GUI
frontend to network manager. Answer those questions and we should be able figure it 
out.

P:s do you have elementary-art ppa active?

Here it goes:

Version in Synaptic: 0.8.1+git.20100809t190028.290dc70-0ubuntu3 (LATEST)

With right click: NetworkManager Applet 0.8.1

Well, this is it... for some reason i loose the wi-fi connection, the network manager icon disappears and there is no wifi connection.

---

### Post by argued.logic on 2011-01-24
> **elidoperezmd said:**
> Here it goes:

Version in Synaptic: 0.8.1+git.20100809t190028.290dc70-0ubuntu3 (LATEST)

With right click: NetworkManager Applet 0.8.1

Well, this is it... for some reason i loose the wi-fi connection, the network manager icon disappears and there is no wifi connection.

That seems to be correct versions you have there. Any error messages if you start the applet from terminal?

---

### Post by elidoperezmd on 2011-01-24
> **argued.logic said:**
> That seems to be correct versions you have there. Any error messages if you start the applet from terminal?

Only this:

elidoperezmd@elidoperezmd:~$ killall nm-applet
elidoperezmd@elidoperezmd:~$ sudo nm-applet --sm-disable
[sudo] password for elidoperezmd: 
** Message: applet now removed from the notification area
** Message: applet now embedded in the notification area
** Message: <info>  No keyring secrets found for Auto Private wireless network/802-11-wireless-security; asking user.

** (nm-applet:25846): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:25846): DEBUG: foo_client_state_changed_cb
** Message: <info>  New secrets for Auto Private wireless network/802-11-wireless-security requested; ask the user

** (nm-applet:25846): DEBUG: foo_client_state_changed_cb

---

### Post by argued.logic on 2011-01-25
> **elidoperezmd said:**
> Only this:

elidoperezmd@elidoperezmd:~$ killall nm-applet
elidoperezmd@elidoperezmd:~$ sudo nm-applet --sm-disable
[sudo] password for elidoperezmd: 
** Message: applet now removed from the notification area
** Message: applet now embedded in the notification area
** Message: <info>  No keyring secrets found for Auto Private wireless network/802-11-wireless-security; asking user.

** (nm-applet:25846): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:25846): DEBUG: foo_client_state_changed_cb
** Message: <info>  New secrets for Auto Private wireless network/802-11-wireless-security requested; ask the user

** (nm-applet:25846): DEBUG: foo_client_state_changed_cb

As this doesn't tell me anything other than you are prompted for password on new wireless connection I ll leave the word to others with higher understanding in what is going on with the network manager at this state. Few things I ve picked up from other threads that might be causing nm act/behave in "wrong" way I could share since it doesn't hurt trying right.
So assume you don't have the mem-leak issue and you are able to connect to your networks with the exception of nm-applet crashing in random.
Check to see under "edit" in either network connection if it is "available to all users". If yes then un-mark and logout. Also monitoring the network manager for "other" errors could be a good idea since it could lead you closer to an actual answer.
In rare cases that I ve read about, creating a new user account solves all issues with gconf since you are practically starting from scratch. Good luck to you and lets hope others jump on this thread leading you to a solution.

---

