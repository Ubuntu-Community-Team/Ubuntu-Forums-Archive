---
title: "SSH remote access kubuntu desktop"
date: 2010-07-27
forum: Networking &amp; Wireless
---

### Post by LAD29 on 2010-07-27
Hi,

I've been looking for an alternate way to remote control my Kubuntu test machine other than via VNC as the performance is awful.

I've SSH server set up and can connect via SSH just fine.

Having read various forums and topics via google I've got so far as having the following:

ssh -X -C -A -c blowfish *username*@*serverIP* gnome-panel.

Now, when I run this I get a bash error saying:-

bash: gnome-panel: command not found.

I was thinking this is something to do with using Kubuntu and not Ubuntu (I'm quite new at Linux so am learning from doing)?

Before I put in the '-A' I was getting an .Xauthority access error, so that seems to have solved that.

From my limited knowledge then I'm thinking what I'm missing is the correct step to send X over SSH?

Is that correct or am I completely off base here?

Cheers.

---

### Post by P4man on 2010-07-27
gnome-panel is for gnome. Kubuntu doesnt have gnome, it has KDE. I dont know the KDE equivalent though..
But you can try any KDE app and see if that works; like kate.

---

### Post by LAD29 on 2010-07-27
> **P4man said:**
> gnome-panel is for gnome. Kubuntu doesnt have gnome, it has KDE. I dont know the KDE equivalent though..


That's what I thought.  I can't seem to find a reference to an equivelant either.  I've tried a couple of things, can't remember what one was called, the other was called 'pulse' if I remember correct.  Came up with the same error (obv with the different app named instead).

> **P4man said:**
> But you can try any KDE app and see if that works; like kate.

Good idea for a test, but I want to control the full desktop ideally, not just have access to one specific app.

Cheers.

---

### Post by P4man on 2010-07-27
Try with "startkde".

---

### Post by LAD29 on 2010-07-27
ooh

Could be making progress here P4man.

This time after a short pause I got the following message in terminal:-

"KDE seems to be already running on this display."

A few seconds later a little xmessage window pops with the same message in.

I'm guessing then, but might there be a way to open another KDE session in a different display?

---

### Post by LAD29 on 2010-07-27
Oh yeah, by the way, I got Kate to launch ok so definately getting through.

---

### Post by P4man on 2010-07-27
ah.. well; this will work if KDE isnt running on the server.

Someone more familiar with KDE might give you the right answer, and it could be possible to run KDE twice; but a brute force way could be ssh-ing in to the machine and then restarting KDM.

```
sudo restart kdm
```

Mostly guessing here as Im a gnome-guy. If this works; it  will log out the user on the remote machine and lose any unsaved work.

edit: btw in older KDE releases the equivalent to gnome-panel would be kicker. see what happens when you try that?

---

### Post by LAD29 on 2010-07-27
> **P4man said:**
> 
edit: btw in older KDE releases the equivalent to gnome-panel would be kicker. see what happens when you try that?

Kicker- that's the one! That's what I tried earlier with the other one being plasma not pulse.  Both didn't work.

I'll try the idea about kicking out the current logged in user.

Thanks for the help.

---

