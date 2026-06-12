---
title: "Mythfrontend does not respond to input"
date: 2009-04-26
forum: Mythbuntu
---

### Post by dibuntux on 2009-04-26
This is odd. It's just that mythfrontend does not receive input, nor from keyboard or remote, becouse a terminal windows is open on the desktop behind it. 

If I Alt-Tab to the open terminal window, I can input text; if I Alt-Tab again, then mythfrontend works normally.

I've always left a terminal window open, so I can easily restart mythfrontend if it crashes, choosing it from the list of recent terminal inputs.

Since mythfrontend is started automatically in the session, and is presented on screen, the input also should be connected with the foreground program...

I've upgraded OK from 8.10, and just got this annoying problem.

Any ideas? TIA

---

### Post by cat5 on 2009-04-26
I have the same problem, guess I should not have upgraded to .22 trunk at the same time I was doing an upgrade to 9.04.

I've traced it back (at least on my own comp) - that mythtv-video is looking for libmyth-python, which requires << python-2.6 and I have 2.6.2 installed.

I believe libmyth-python is where keybindings are as well... could be wrong.. cause I know I can press "right" on my keyboard, then enter, and a new menu comes up, though I don't have any "visual" cues to tell me it worked.


In anycase, I'm personally stuck on libmyth-python + mythtv-video's not being able to be installed due to the python versioning issues.

I'm using the PPA's from here:

[http://ppa.launchpad.net/mythbuntu/ppa/](http://ppa.launchpad.net/mythbuntu/ppa/)

version 0.21+fixes - svn20445 as of this morning.

EDIT: corrected version - was not on .22 trunk afterall...

---

### Post by superm1 on 2009-04-26
> **dibuntux said:**
> This is odd. It's just that mythfrontend does not receive input, nor from keyboard or remote, becouse a terminal windows is open on the desktop behind it. 

If I Alt-Tab to the open terminal window, I can input text; if I Alt-Tab again, then mythfrontend works normally.

I've always left a terminal window open, so I can easily restart mythfrontend if it crashes, choosing it from the list of recent terminal inputs.

Since mythfrontend is started automatically in the session, and is presented on screen, the input also should be connected with the foreground program...

I've upgraded OK from 8.10, and just got this annoying problem.

Any ideas? TIA
Are you on trunk? There is a known problem with this on trunk.

---

### Post by superm1 on 2009-04-26
> **cat5 said:**
> I have the same problem, guess I should not have upgraded to .22 trunk at the same time I was doing an upgrade to 9.04.

I've traced it back (at least on my own comp) - that mythtv-video is looking for libmyth-python, which requires << python-2.6 and I have 2.6.2 installed.

I believe libmyth-python is where keybindings are as well... could be wrong.. cause I know I can press "right" on my keyboard, then enter, and a new menu comes up, though I don't have any "visual" cues to tell me it worked.


In anycase, I'm personally stuck on libmyth-python + mythtv-video's not being able to be installed due to the python versioning issues.

I'm using the PPA's from here:

[http://ppa.launchpad.net/mythbuntu/ppa/](http://ppa.launchpad.net/mythbuntu/ppa/)

version 0.21+fixes - svn20445 as of this morning.

EDIT: corrected version - was not on .22 trunk afterall...
If they can't be installed you likely have the wrong repo specified.  You *must* make sure hardy goes with hardy, intrepid with intrepid and jaunty with jaunty.

Running a dpkg-reconfigure mythbuntu-weekly will clear out the repo and put the right one in (assuming you installed from the mythbuntu-weekly package)

---

### Post by dibuntux on 2009-04-27
No, I'm not on trunk. Just a plain upgrade of 8.10 > 9.04.

Anyway, I partially solved this by closing the terminal window underneath. Still is annoying. If mythfrontend crash I have to get up from the sofa and go mangling with mouse & keyboard. BTW, is there a keyboard shortcut to recall a terminal window? 
Thanks to all!

---

### Post by dibuntux on 2009-05-12
No - I still have the problem. The terminal window in the background remains open at every start up and I have to manually AltTab to get MythTV main menu in the foreground.

The strange is that when it starts it seems to already be in foreground - you realize it is not because input, either vie remote or keyboard, does not work.

Any ideas? TIA

---

### Post by Dewey_Oxberger on 2009-05-12
I have a remote keyboard.  I bailed on all the IR remote stuff.  The keyboard works great and you can't loose it in the sofa cushions.

Anyway, ctrl + alt + F6 gets you to a terminal - but not in X.  ctrl + alt + F7 is the X session that has your myth.  ctrl + alt + F8 is the boot session.

---

