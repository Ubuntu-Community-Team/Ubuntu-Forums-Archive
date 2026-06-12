---
title: "Desktop Effects are breaking by system"
date: 2007-04-21
forum: Multimedia &amp; Video
---

### Post by erikcw on 2007-04-21
Hi all,

I enabled desktop effects on my fresh install of Feisty.  Everything worked fine.

I then restored my Edgy home directory from backup (I had been using beryl with Edgy).  Now, windows won't come into focus, and/or widgets won't display inside of widows.  I can't even turn desktop effects off, because when I open the window, it's just a grey canvas.

How can I turn off desktop effects from the command line?

Why would it be working before I restorted my home directory?  I deleted the .beyrl config files flom my ~.

Thanks for your help!
Erik

---

### Post by jwjazz on 2007-04-29
If you want to turn off desktop effects from the command line, I am assuming you cannot see anything on your desktop, you may have a white or black screen.
First, restart by pressing CTRL- left ALT-Backspace
You will see a login screen.
before logging in, click the button for options at the lower right
then click change session
You may have gotten this far already, but perhaps another reader is having the same problem, so,
Select failsafe terminal
now login
at the prompt type:
gconf-editor
this will open up  the registry
now select Desktop->Gnome->Applications->window_manager
the current and default key values will probably say /usr/bin/compiz
select the key value by clicking once on the key value
you can completely erase **both** the default and current values and when ubuntu restarts it will automatically fill in these vaules with /usr/bin/metacity
You can alternatively enter in /usr/bin/metacity for [B]both[B] the current and default values.
Now restart (Ctrl_left Alt-Backspace) and at the login screen change your session back to xclient and login.

everything's back to normal (if you left the key values blank, it will take a second for everything to appear normal)
hope this helps

---

### Post by superdexter on 2007-05-01
That is a great process to recover and works fine.  I'm curious on how you allow a non-admin user logging into the 2nd X session to have compiz turned on without going all white screen.

---

### Post by jwjazz on 2007-05-01
> **superdexter said:**
> That is a great process to recover and works fine.  I'm curious on how you allow a non-admin user logging into the 2nd X session to have compiz turned on without going all white screen.
I don't understand your question.  I was logging in as an admin user, and on the second Xclient session that you are referring to, I had already turned off compiz by changing the key value to /usr/bin/metacity in the earlier failsafe terminal session.  So I don't understand what you are asking.  Maybe you can rephrase the question.  
I just had an idea of what you may be asking.  let me try to state your question.  How do I login as a non-admin user with compiz turned on and NOT have the screen go completely white?
If that is your question than I think the answer is that it doesn't matter if you are admin or not.  As long as compiz is turned on and your graphics card does not support desktop effects, you will have a white screen.
I hope this helps.

---

### Post by superdexter on 2007-05-02
Really close :).

I've played with it a bit more and can narrow down my question.

How may I log into the second Xclient session with compiz enabled without causing total white screen.

It seems admin vs. non-admin makes no difference.  Likewise, even if the effects are disabled on the first Xclient session, when I log into the second and enable effects, total white screen.

Is there some xorg.conf changes to be made to allow any Xclient session (2nd, 3rd, etc) to use effects?

Thanks,

---

### Post by jwjazz on 2007-05-02
Unfortunately I don't know the answer to your question.  I am quite new to linux.

---

### Post by c^2 on 2008-03-28
disabling the desktop effects worked wonders for me! thnx so much!
much appreciated

---

