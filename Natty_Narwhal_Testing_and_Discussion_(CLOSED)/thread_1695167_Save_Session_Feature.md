---
title: "Save Session Feature"
date: 2011-02-25
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by brianafischer on 2011-02-25
I am trying to find the "Session Saving" feature in Natty 11.04.  I would like my session to be saved and restored upon reboot.

Is this possible in Natty?  I cannot seem to find any mention of this.

---

### Post by seeker5528 on 2011-02-25
Doesn't seem to be a way that I can find. 

My searching on Google didn't bring me to anything indicating this functionality would intentionally be removed in Gnome. Maybe someone with better google-fu than me could find something.

Typing 'gnome-session-properties' at the command line brings up the same dialog for choosing start up applications as when you go into the control panel and choose to modify them, no options there. Opening a terminal window and typing 'gnome-session-save' seems to have no effect with or without any type of logout/shutdown options specified.

Unless somebody knows or can find something we are left to guess whether this capability was intentially omitted upstream, was lost in transition due to issues upstream and will re-appear later, or temporarily lost in Natty because while there is Gnome 3 stuff being added, the full migration to the Gnome 3 base won't happen until later.

The Gnome 3 stuff is not final yet so it could be a capability that is intended to be there but currently borked because of some settings issue, component mismatch, etc...

Without any further information indicating the save session was intentionally removed/disabled I would file a bug report if one doesn't already exist. And once one is found/created post a link to it and try to get other people who care about that capability to follow the link and check the box to indicate they are also affected by the issue.

Later, Seeker

---

### Post by mc4man on 2011-02-25
Didn't read thru because I've no interest in session saving, maybe look here
[http://www.linux-archive.org/ubuntu-desktop/478109-gnome-session-saving-dropped-natty.html](http://www.linux-archive.org/ubuntu-desktop/478109-gnome-session-saving-dropped-natty.html)

---

### Post by seeker5528 on 2011-02-25
Guess that answers that then.

I never really saw the sense in saving the session in gnome if they are not going to to more than start the applications you previously had running, otherwise you get more predictable result just adding the stuff to your start up.

It was a feature that I used in other window manager environments in the past where 'save session' was the official/semi-official method of setting what you wanted running at startup, but typically in those environments it worked better than it ever did for me with the Gnome Desktop.

That's not to say I agree with decision to disable session saving, but I can see where the Ubuntu devs are coming from in making that decision.

Later, Seeker

---

### Post by brianafischer on 2011-02-25
mc4man: Thanks for the link.  It appears that you are better friends with google than I am...


seeker5528: I could use the session saving feature quite a bit.  Granted that the restored desktop should not just open the applications, but return it to the exact state saved.  It is very nice feature when an update requires a reboot.  It usually takes a few minutes to manually restore the current desktop state.  After all, a computer should be a productivity tool!

---

### Post by seeker5528 on 2011-02-25
> **brianafischer said:**
> Granted that the restored desktop should not just open the applications, but return it to the exact state saved.

Doing that in any meaningful way is a big ordeal, I don't see it happening soon.

When you put the computer to sleep or hibernation you know nothing is going to be running so you can just save the entire state of the running system to an image and reload that image when you come back from hibernation.

In saving the session no assumption can be made about how the state of the system might change in between when the session was saved and the next time the session is loaded again so you can't just take a snapshot of the running state and load it back in. 

The first thing you need is some standardization in the session management itself so each environment doesn't have to handle things it's own way, ways to blacklist things that shouldn't load depending on the environment or session profile use with an environment and to provide standardized methods for the session manager to talk to applications and vice versa.

Then the applications have to have some support so they can communicate to the session manager the information that needs to be passed back to them when they get reloaded so you end up at the same place you were when the session was saved, with or without any unsaved data there may have been when the session was saved.

That would be the ideal anyway, there never really seemed to be much progress along that path to allow more advanced capabilities.

If you are just looking at Gnome and it's normal list of stuff, the thing that always caused me problems was when you have something in your start up, you save the session so now they are in the start up and the saved session and when you log in the next time you get complaints and sometimes some things that just don't work right because things are attempting to be loaded twice or the entries in the saved session only know what was loaded not what options should be used when loading it. 

On that front things seems like they must have improved a bit since the things to start up are usually .desktop files that are created in or placed in either the standard start up directory or the gnome/KDE/etc... specific one. 

If you combine the quirkiness of gnome session management with different environments that use the gnome session manager then apparently you have what the Ubuntu devs were talking about where if you save the session while running one environment then start a different environment you end up with things running the shouldn't be and things the should have been started that weren't.

Generally speaking KDE seems to handle session saving better, but you don't have that same situation where there are other environments using the KDE session manager in the way the gnome session manager gets used in Ubuntu in different environments.

Maybe after the Gnome 3 development settles down a bit and Unity development settles down a bit they can get it working again?

Later, Seeker

---

### Post by yamameguy on 2011-04-14
Seeker5528 wrote:

"That's not to say I agree with decision to disable session saving, but I can see where the Ubuntu devs are coming from in making that decision."

I can't, really. The gist of what they said in the link provided by mc4man is that "Saving the Gnome session isn't perfect, so we're going to chuck it all together." The astonishing disconnect in that idea from both what most people expect from saving the session (that it will restart the apps, not that it will restore the exact state) and from the truest engineering statement of all time - that the perfect is the enemy of the good - is simply astonishing.

I run 12 virtual desktops. Apps open in each. Having to manually restart those is a PITA. I use Linux both personally and professionally, and just upgraded to Natty and now am most unhappy. Lack of saving the session is a real dealbreaker, and it offsets the wonderful work they did by making Mac-style global menus work perfectly, even with Thunderbird and Firefox. I salute them for that.

Maybe all the time they wasted making the impossibily hideous and unusable netbook interface the default (my kids have Ubuntu netbooks, but they couldn't stand it there either, so I set them up with Gnome and Avant Window Navigator), could have been better spent making the session save work better (or not; it's good enough already, at least for most people).

For a workaround, I have it in mind to either compile from source and make and immutable symlink to the standard gnome-session-properties, or force-install a mainline debian package, and make its binaries immutable. I'm probably less likely to run into problems with the first approach, but the second approach is a lot less work.

Failing that, I'll be taking another look at Kubuntu, which I stopped using a while back because of poor multihead support and the fact that AWN works a lot better running under Gnome than it does under KDE. The last time I booted a Kubunt like CD the multihead support was a lot better.

Hmm, maybe I'll try Kubuntu first. In most other respects it was better than Gnome anyway, but lacked the great artwork done in Ubuntu.

---

### Post by seeker5528 on 2011-04-14
> **yamameguy said:**
> I can't, really. The gist of what they said in the link provided by mc4man is that "Saving the Gnome session isn't perfect, so we're going to chuck it all together." The astonishing disconnect in that idea from both what most people expect from saving the session (that it will restart the apps, not that it will restore the exact state)

What I got out of it was that the main issue was that session saving is a really bad citizen if you have multiple environments that use gnome-session and you switch between them. Any other excuses are just padding on top of the main issue.

> I run 12 virtual desktops. Apps open in each. Having to manually restart those is a PITA. I use Linux both personally and professionally, and just upgraded to Natty and now am most unhappy. Lack of saving the session is a real dealbreaker, and it offsets the wonderful work they did by making Mac-style global menus work perfectly, even with Thunderbird and Firefox. I salute them for that.

...snip....

> Hmm, maybe I'll try Kubuntu first. In most other respects it was better than Gnome anyway, but lacked the great artwork done in Ubuntu.

It always seemed to me like the session saving in KDE worked better than in Gnome.

Sounds like you could possibly benefit from the 'Activity' feature as well.

An activity in KDE is a little like a mini-session inside the main session, or comparing an activity to a run level might be a better comparison, haven't played with it enough to have a thorough grasp of what does and doesn't work.

If you create multiple activities, each one is customizable the same way you would normally customize your desktops, if you switch to another activity and switch back, the applications that you had running when you last used that activity will be started again on the same desktop they were on. From the little I played with it, it seemed like when you switch from one activity to another *all* the applications get killed then the ones that were running in the activity you are switching to started, even if both activities had some of the same applications on the same desktops.

Later, Seeker

---

### Post by cariboo on 2011-04-14
There is a way to do what you want in Unity, I saw a solution a couple of days ago, as I was thinking the same thing. I'll see if I can find it.

---

