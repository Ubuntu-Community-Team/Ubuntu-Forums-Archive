---
title: "Synaptic won't run"
date: 2011-04-01
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by osarusan on 2011-04-01
When I try to run Synaptic from the administration menu I get a different password box than I normally do, and when I enter my password it always comes up incorrect.

I can run synaptic from the terminal using gksudo synaptic, but then I get the following error message before it runs:

(gksudo:18829): Bonobo-WARNING **: Bonobo must be initialized before use

(update-apt-xapian-index:18840): Bonobo-WARNING **: Bonobo must be initialized before use

Any ideas what this means or how to fix it?

---

### Post by osarusan on 2011-04-02
I've now noticed this is not only confined to Synaptic, but a number of programs. They all give the same different password dialogue, which looks like a keyring password dialogue or something, and when I run them in the terminal they give a bonobo error message.....

---

### Post by cbowman57 on 2011-04-02
Try installing (or reinstalling) apt-xapian-index from the terminal.

---

### Post by osarusan on 2011-04-02
I purged and reinstalled, during the installation I got this message:

(update-apt-xapian-index:10703): Bonobo-WARNING **: Bonobo must be initialized before use

The other problem still exists too.

---

### Post by mc4man on 2011-04-02
haven't seen any thing like that here on natty, though does remind of something
Open gconf-editor > apps > gksu and make sure sudo mode is enabled, if not then  enable and restart

---

### Post by cbowman57 on 2011-04-02
Wow, the bonobo libraries are linked to everything.  If you could get in to synaptic it might be possible to do a re-installation but I guess that's an option we don't have.

Is this a fresh installation, beta, old installation that has seen numerous upgrades?  I'm not familiar with international versions personally.  I wonder if it's tied to your locale?  I'm making an assumption that it was installed with the native Japanese language support.

Might have to resort to re-installing the entire system and see if that cures it.  Choose the "do not format" option to preserve your settings & files.

Sorry I can't be more help.

---

### Post by osarusan on 2011-04-02
I can get into Synaptic if I use the terminal to run. The problem only arises when I try to run programs from the Gnome menu or using Synapse or some other thing.

I can still *use* everything, but I have to do it in a roundabout way that tells me something is definitely wrong.

This was an old installation that I upgraded to 11.04. The upgrade didn't go well and was really screwy for a while. Last night I uninstalled almost every package and reinstalled them this morning, and it fixed every problem I was having -- except it added this odd new problem.

I'm running the US English localization, even though I am in Japan.

I'm reserving the reinstall for the last resort... I hope it doesn't come to that... If there's a way to fix Bonobo from Synaptic I would like to try.

---

### Post by cbowman57 on 2011-04-02
Ok, then I'd get into synaptic and do a search for every file with bonobo in it's name or description and mark for re-installation.  Hit apply and pray that fixes the problem.

Good luck Osarusan.

---

### Post by ranch hand on 2011-04-02
You could try removing it and then reinstalling.   I would check to see if there are any left over files after the removal.  Check that under Status (lower left on synaptics screeen).

You could check your "hidden" files in your home folder too for a config file for Bonobo.  Just delete it before you reinstall.

---

### Post by osarusan on 2011-04-02
mc4man's suggestion about gconf-editor worked partially -- the sudo option was not checked, so I checked it, and now I can run Synaptic from the menu.

However, when I run it from a terminal I still get the Bonobo error, and I am also hit with a string of login/keyring prompts when I log in, and entering my password doesnt seem to affect them at all.

I'll search for the bonobo config file and through the bonobo files and try reinstalling them.

---

### Post by osarusan on 2011-04-02
Well... reinstalling them didn't fix the error messages either. :-\

---

### Post by cbowman57 on 2011-04-02
Bummer.

---

### Post by Harry33 on 2011-04-02
> **cbowman57 said:**
> Bummer.

I do not think this is actually related to Synaptic.
The error message appears because of the problems with gksudo, possibly a GTK+2 or dbus problem.
So, not a Synaptic nor a Bonobo problem.
Actually packages libbonobo* are related to the package gnome-power-manager and its applet package (libpanel-applet2-0).

---

### Post by osarusan on 2011-04-02
Thanks for your help, Harry33. I reinstalled gnome-power-manager and the libpanel-applet2-0 and 3-0 and the problems with the keyring is now fixed. I can run Synaptic fine as well with no issues.

However... the Bonobo error message is still coming up. When I installing things through Synaptic and look at the terminal output, I see this error message popping up too.

Bit by bit things are getting solved here, but there is still some underlying issue......

---

### Post by osarusan on 2011-04-02
Alright! I think I found a solution!
After googling around for those bonobo error messages, I found this:
[https://bugzilla.redhat.com/show_bug.cgi?id=632935](https://bugzilla.redhat.com/show_bug.cgi?id=632935)

I followed the instructions in the last post and checked in gconf, and I disabled accessibility. The error no longer appears.

Question: should accessibility be enabled?? Or was that some fluke?

---

### Post by Harry33 on 2011-04-02
> **osarusan said:**
> Alright! I think I found a solution!
After googling around for those bonobo error messages, I found this:
[https://bugzilla.redhat.com/show_bug.cgi?id=632935](https://bugzilla.redhat.com/show_bug.cgi?id=632935)

I followed the instructions in the last post and checked in gconf, and I disabled accessibility. The error no longer appears.

Question: should accessibility be enabled?? Or was that some fluke?

So, you did this:
> I would guess that you perhaps have accessibility
turned on, and are using the old, bonobo-based accessibility stack ?

It says the bonobo-based accessibility schemes are old and thus do not work right.
Well, you may of course disable accessibility schemes if you do not use them.

---

### Post by cbowman57 on 2011-04-02
> **osarusan said:**
> Alright! I think I found a solution!
.. [https://bugzilla.redhat.com/show_bug.cgi?id=632935](https://bugzilla.redhat.com/show_bug.cgi?id=632935)

I followed the instructions in the last post and checked in gconf, and I disabled accessibility. The error no longer appears.

...

Outstanding!  Glad you found the cure, I'll file this fix away in case I ever run into a similar problem.

---

