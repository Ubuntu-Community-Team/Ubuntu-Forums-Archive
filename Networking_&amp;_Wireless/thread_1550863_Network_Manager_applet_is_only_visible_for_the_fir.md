---
title: "Network Manager applet is only visible for the first logged-in user"
date: 2010-08-11
forum: Networking &amp; Wireless
---

### Post by Birion on 2010-08-11
I'm currently setting up a (to-be) family computer, and noticed that if I switch user accounts, the Network Manager applet is only on the panel of the first user (even if I log out of that account). Is there a way to enable it for every account (so that other people can reconnect to our rather unstable connection)?

---

### Post by ajgreeny on 2010-08-11
I think each user will have to add the "Notification area" to their panel.

---

### Post by Birion on 2010-08-11
Nope, that's not it. Every user has the Notification Area on their respective panel (it's there by default, I believe).

But it looks like I may not have properly explained the problem. Let's imagine that I have three accounts on the computer, let's call them Alice, Bob, and Chris.

The computer turns on, Alice logs in. Alice's panel has the Network Manager applet. Bob come by later, wants to check his email, so he logs into his account. Bob's panel does not have the Network Manager applet. Bob and Alice go out drinking, turn off the computer. Chris comes home later on, turns on the computer, logs into his account. Now Chris's panel has the applet. Alice returns from the pub, logs in and notes that her panel does not have the applet.

I hope with this situation, my problem is a little bit clearer.

---

### Post by ajgreeny on 2010-08-11
Yes, it is thankyou, but unfortunately I do not have any clue about why it's happening that way.

Any idea what happens if the first logged on user logs out before the second logs on, as opposed to what I assume you are talking about, ie two users logged on together?  Does then second logged on user get the NM applet if the first has logged out so that there is only one user.

Also do all users have admin privileges, or is that just the first user?  I'm not sure why that should make any difference, but it was just a sudden thought.

---

### Post by Birion on 2010-08-11
Only one user has admin privileges. I just tried the logging out before logging in and now this account has the applet (Alice had the applet, Alice logged out, Bob logged in, Bob has the applet, Alice logged in and does not have the applet, all of this without restarting).

---

### Post by Vaphell on 2010-08-12
this is a huge fail design-wise. First logged user gets to start network manager successfully and initializes network, 2nd user tries to start it up too but fails hard because there can be only 1 instance of NM globally. If you log out the 1st user, every other logged user will lose network connection as it will go down together with the instance of NM and you need a new session to regain connectivity (new session will start NM successfully). This inherent problem with the net manager kills pretty much any sense of having an option to switch users in a prominent place of user interface.
What's worse is that the problem is known for 2 or 3 years and no fix was applied.


I think the only solid workaround would be to hardcode network parameters in system files (/etc/network/interfaces and /etc/resolv.conf) so running NM is not necessary and connection is up for all after booting up, not after 1st successful login.

[http://blog.jacobodevera.com/2009/07/30/gnome-network-manager-applet-with-multiple-users.html](http://blog.jacobodevera.com/2009/07/30/gnome-network-manager-applet-with-multiple-users.html)

---

### Post by colinvv on 2011-02-16
So... still no answer for this? The network does work for that second user... but I can find no way to initiate a VPN connection without seeing and using the network status. Can I create a 'launcher' for a VPN connection?

---

### Post by walt.smith1960 on 2011-02-16
I'm not positive but try this--for users that can't see network manager, in a terminal type"nm-applet"  I *have* gotten into a state doing this where it worked but closing the terminal disconnected the user.  I see this when being logged in as more than one user on the same machine.  For example, logged into an account with administrative privileges and another user account at the same time.

---

### Post by errrorer on 2011-02-16
I guess, this problem only occurs when the first user is connected to the Internet and your connection is available for all users. Have you tried surf the net in the second account? If not, try so.

Right click on ur network applet and edit connection. Select your connection and click edit. You'ld probably see that the "Available for all users" is checked. 

If its so, it's no problem. when the first user is connected the second user will be able to browse the internet. 

Hope this help. If not, sorry man; I don't know what's going on....

Take Care):P

---

