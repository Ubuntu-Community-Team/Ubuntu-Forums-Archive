---
title: "Strange Firefox Behaviour"
date: 2011-02-11
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by jennybrew on 2011-02-11
Hi all.
Ive done a quick search of this forum and cant find a post addressing this issue but please accept my apologies if I am duplicating something which has already been addressed.
The issue I am seeing relates to multiple instances of Firefox.
Having opened 4 separate instances, one in each virtual desktop, I set one instance to private browsing.
I was subsequently surprised to see the other 3 instances had shut down.
I thought this was an error on my part but was able to replicate the issue again and again.
I didnt think Firefox had showed this behaivour previously but Im willing to be corrected.
 I can only think that separate instances of Firefox are not isolated from each other and share some or all processes.
Is this intended behaviour on the part of Firefox or is it something which deserves reporting as a bug?

Edit to add: It would be so nice to be able to launch multiple instances of applications from the Unity Docky. Is this something for a future release?

---

### Post by mc4man on 2011-02-11
> Edit to add: It would be so nice to be able to launch multiple instances of applications from the Unity Docky. Is this something for a future release?
If you mean Docky the app don't know, if referring to the unity launcher than a middle click on a launcher icon will open a new instance (if you are updated

---

### Post by jennybrew on 2011-02-11
> **mc4man said:**
> If you mean Docky the app don't know, if referring to the unity launcher than a middle click on a launcher icon will open a new instance (if you are updated


Thanks for replying :)
I didnt know about the middle click but , of course, you are right.
Firefox still behaves the same though when one instance set to private browsing

---

### Post by ajgreeny on 2011-02-11
> **jennybrew said:**
> Hi all.
Ive done a quick search of this forum and cant find a post addressing this issue but please accept my apologies if I am duplicating something which has already been addressed.
The issue I am seeing relates to multiple instances of Firefox.
Having opened 4 separate instances, one in each virtual desktop, I set one instance to private browsing.
I was subsequently surprised to see the other 3 instances had shut down.
I thought this was an error on my part but was able to replicate the issue again and again.
I didnt think Firefox had showed this behaviour previously but I'm willing to be corrected.
 I can only think that separate instances of Firefox are not isolated from each other and share some or all processes.
Is this intended behaviour on the part of Firefox or is it something which deserves reporting as a bug?
I can confirm this behaviour of Firefox on my system as well.

---

### Post by seeker5528 on 2011-02-11
> **jennybrew said:**
> Edit to add: It would be so nice to be able to launch multiple instances of applications from the Unity Docky. Is this something for a future release?

I'm sure it was an option when you right click the launcher, but seems to be MIA at the moment.

Later, Seeker

---

### Post by imdead on 2011-02-11
Hi all I was playing with Ubuntu 11.04 Alpha 2 & I got my connection with the wireless but when I tried to use Firefox it says I'm not connected whats up with this?:(

---

### Post by cariboo on 2011-02-11
@imdead

If it's a network problem, you should start a thread of your own. Can you connect with anything else? Chromium, Xchat, Evolution or Thunderbird?

---

### Post by bikeboy on 2011-02-11
Unless I'm mistaken, you're not starting separate instances. You are merely opening new windows. Going into Private mode temporarily starts a new session in which your other windows are hidden. This is the behaviour of Firefox 4 on Ubuntu 10.10 and indeed all other platforms. Would have to check but I think 3.6 was the same.

I don't have an active Natty around to try this but if you can make custom launchers what you need to do is make a new profile (firefox -profilemanager) and set up a launcher for it, along the lines of the following:

```
firefox -no-remote -P "name of privatebrowsing profile"
```.
The -no-remote switch will ensure that it's an actual new instance and can be run independantly of what you're doing in Firefox windows created on the main instance.

---

### Post by jennybrew on 2011-02-12
> **bikeboy said:**
> Unless I'm mistaken, you're not starting separate instances. You are merely opening new windows. Going into Private mode temporarily starts a new session in which your other windows are hidden. This is the behaviour of Firefox 4 on Ubuntu 10.10 and indeed all other platforms. Would have to check but I think 3.6 was the same.

I don't have an active Natty around to try this but if you can make custom launchers what you need to do is make a new profile (firefox -profilemanager) and set up a launcher for it, along the lines of the following:

```
firefox -no-remote -P "name of privatebrowsing profile"
```.
The -no-remote switch will ensure that it's an actual new instance and can be run independantly of what you're doing in Firefox windows created on the main instance.

OK ..so there is a fix. Many thanks for providing how to do it! Much appreciated.
However, Im not sure if folks would think this is reasonable on a 2011 system hence the reason I asked if its a bug or if its designed behaviour:)
Is this worth the while posting as a bug or is it worth begging for a rethink ?
I really do believe most people would be disappointed at what seems to be the default behaviour re: mutiple   instances. At the very least the advice given in the sticky for this forum is misleading!!

Edited to add: yes I have just checked this out in 10.10 and it is exactly how you say.
I now need to check it out on Windows because I have some difficulty believing Mozilla would think this normal or acceptable.

Weird or what? Hopefully this is not an Ubuntu problem but a Mozilla problem
Keep smiling :)

---

### Post by bikeboy on 2011-02-12
It's the same on Windows. Clicking the shortcut opens another window rather than a separate instance. Always has. The two reasons I can think for this are a) most people (think really basic home user) are *probably* just clicking it to get another window in the easiest way they know how. They don't care about what's going on in the background. That's speculation on my part though; b) Given the profile system for user data, the only safe way to open two instances is with two profiles. I guess they could add something where starting the executable again automatically creates a temporary duplicate of your profile (so you have access to usual bookmarks etc.). That might cause issues with lots of disk I/O on startup though.

There has been talk of completely re-working the profile manager but that has been delayed until after Fx4.

The other thing to consider is what Mozilla thought would be the primary use cases of the Private Browsing mode. Perhaps the separate session was implemented to stop you accidentally doing something in a non-private window when you intended to keep that private. I never read the bug reports to see the implementation details.

I'm almost certain the behaviour is by-design rather than a 'bug' as such. Unless there was a technical limitation that made them do it that way. Nevertheless, you can use their bugzilla ([https://bugzilla.mozilla.org/](https://bugzilla.mozilla.org/)) to both search for discussion and if you feel so inclined, put in a reasoned suggestion for a change in behaviour.

---

### Post by jennybrew on 2011-02-13
> **bikeboy said:**
> 
I'm almost certain the behaviour is by-design rather than a 'bug' as such.

Well that certainly seems to be the case.
I shouldnt complain about something working as designed. However if the design behaviour does suit it makes sense to try another browser. 
Thanks for the replies

---

### Post by dino99 on 2011-02-13
As your private data can be found (logged, ram) within a workplace, dont matter what browser is, each time you open a private browsing, aka a new session, the others (non private) need to be closed, logical.

---

