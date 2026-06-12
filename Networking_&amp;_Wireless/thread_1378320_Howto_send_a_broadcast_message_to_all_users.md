---
title: "Howto send a broadcast message to all users?"
date: 2010-01-11
forum: Networking &amp; Wireless
---

### Post by jackel7007 on 2010-01-11
I'm looking for a solution to broadcast messages on the network.
All systems are Linux / Ubuntu.

It would be used in case the server has to be rebooted.
It saves me a walk to every office in the building.

---

### Post by jackel7007 on 2010-01-14
So far I have found a sort of solution.
This solution uses a combination of samba and linpopup.

Since we are only using Ubuntu in our network, we don't want to install samba. 
(Just for messaging purposes).

So anybody knows any other solution?
Maybe we could use a messenger like tool, but it has to popup on top of everything.
And we need the option to sent to all users at once.

---

### Post by wojox on 2010-01-14
```
man shutdown
```

You can set the time and broadcast a message to all users logged on.

---

### Post by jackel7007 on 2010-01-25
Thanks for your reply, but it's not what I meant.
Problem is, that people are working on our server with applications like Frontaccounting, Sugarcrm and Xoops.

So I would like to be able to broadcast a message from this server to all clients on the network. Using this, I can inform people of the fact that the server will for example be rebooted in 15 minutes. 

The people who need to receive the message are not logged in on the system using SSH or whatever. All of the applications used by the users are web-based. So their in fact apache users and they don't have an user account on the system.

---

### Post by Iowan on 2010-01-25
Dunno if it's what you're looking for - but try **man wall**.

---

### Post by jackel7007 on 2010-02-03
Doesn't Man Wall only sent a message to the users logged in on the system?
(either local or remote)

From what i tested this doesn't sent a message to the users using the web-server.
(our users are constantly using SugarCRM, so I want to sent a broadcast to them in case of server reboot)

---

### Post by jackel7007 on 2010-03-11
Nobody? :cry:

I would swear that what i want to accomplish, is not that odd.
I can't imagine that in the bigger companies the system administrator walks or calls to everyone to inform them about the upcoming server maintenance?

It doesn't matter what program i use, or how i have to use it, the only requirment is that i can type the message once, and so it is displayed to all desktops in the company.

---

### Post by inobe on 2010-03-11
> **jackel7007 said:**
> Nobody? :cry:

I would swear that what i want to accomplish, is not that odd.
I can't imagine that in the bigger companies the system administrator walks or calls to everyone to inform them about the upcoming server maintenance?

It doesn't matter what program i use, or how i have to use it, the only requirment is that i can type the message once, and so it is displayed to all desktops in the company.

sure

install pidgin, add an account, select bonjour.

it basically uses zeroconf, it's a simple lan/ ip messenger.

if that's not what you need i can have a look around ?

---

### Post by AggravatedGestalt on 2011-01-12
> **inobe said:**
> sure

install pidgin, add an account, select bonjour.

it basically uses zeroconf, it's a simple lan/ ip messenger.

if that's not what you need i can have a look around ?

Well, no hijacking intended, but without installing anything, is there another way? I admit, this may seem dumb, but for example, I have a logged-in "safety" user via ctrl+alt+F2, and when I alt+F7 to my admin user and broadcast a message with wall, the "safety" user receives no message despite receiving the message on the admin user's terminal. If this is off subject, please say so, and I will edit my post to blank.
Edit: I had to: 
**mesg y**
as the "safety" user. Is there a way to force messages to all users even if messages are set to n?

---

### Post by matt_symes on 2011-01-12
Hi

> Well, no hijacking intended

Nicely hijacked ;) Usually frowned upon in many forums though. Anyways

Check that your Saftey user has messages from wall allowed.

```
mesg
```

to check. It will return 'is y' or 'is n'.

```
mesg y
```

to allow.

```
mesg n
```

to disallow.

To test.

```
echo "testing 123" | wall
```

Kind regards

---

### Post by Monery on 2011-03-03
I was able to send a message using wall. of course you need to use sudo unless your logged in as root. The problem I have with this is that it only sends it to a open bash window. I been using FreeNX for GUI. If the user has a bash window open, then everything works great, sad thing is if no bash, no message. Is there a way to make this work with remote GUI users?

---

