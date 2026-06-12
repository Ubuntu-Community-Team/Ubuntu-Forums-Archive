---
title: "usermod - I guess it needs some attention"
date: 2010-06-14
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by recluce on 2010-06-14
Most newcomers to Ubuntu don't realize how hard it is to change the username (aka short name or nickname) of an exisiting account - which leads to usernames not carefully chosen and the desire to change them. Why some people might argue the necessity of changing a username, this is really besides the point as long as Ubuntu comes with a command line tool to do this - and without sufficient warnings against using that tool.

What happens, if you use usermod? Let us assume that you used it from another account and correctly renamed the user and home directory. Now, the system *seems* to be stable and working correctly, but the borkage may already be done. 

When I changed the username of my Lucid installations (when moving Lucid into production and migrating my data from Jaunty) from stephan-test to stephan (and renaming my home folder accordingly) the following things broke:

- WINE
- K3B
- GNOME (or parts of it)

WINE did no longer work for most applications, which was not a surprise after I looked at the various wine registy files: the former "stephan-test" home folder was hardcoded in various places there, basically breaking any Windows application using that method to find its paths.

K3B could no longer find a home directory, no obvious ways could be found to correct this.

GNOME and all the related systems: junk in the applications menu ("Other") that could not be deleted and most confusing: no visual effects and no buttons in the title bar of windows after each and every logon. The buttons did reappear after manually resetting the visual effects (extra or whatever else), but only for the current session.

Probably other things borked as well, but I had enough at that point - the only remedy being to delete my user and home folder (after saving relevant data, of course) and making a new user account.

Obviously, usernames cannot be changed for practical purposes at this point in time. So what can be done? Some ideas:

Short term:

1.) remove usermod

2.) alternatively, limit its functionality to exclude renaming the home directory

3.) if 2.) seems still excessive, include prominent warnings, both in the man page and before executing dangerous actions. Something like "Changing the name of your home folder is very likely to break your system and is NOT advised. Do not proceed unless you are sure that you have no packages installed that depend on your current home folder name." Type "Yes" to continue or anything else to cancel.

Long term:

Adopt a policy that requires packages to do relative references to the home folder only. In WINE for example, reference "DesktopFile"="~/.local/share/applications/wine-extension-chm.desktop" instead of "DesktopFile"="/home/stephan/.local/share/applications/wine-extension-chm.desktop", for example.

While the problem is not specific to Maverick, changes can only happen here and in the future of Ubuntu. I would like to see your opinions. Do you think this is worth opening a bug on Launchpad?

---

### Post by recluce on 2010-06-15
*** BUMP ***

Nobody cares for a tool included in Ubuntu that can totally bork the system? Somehow, the Lucid development forum was a bit more lively...

---

### Post by chrisccoulson on 2010-06-15
> **recluce said:**
> *** BUMP ***

Nobody cares for a tool included in Ubuntu that can totally bork the system? Somehow, the Lucid development forum was a bit more lively...

Hmmmm, there are plenty of tools that can "bork" the system when used improperly - eg, rm, dd, fsck, fdisk, mkfs etc. I'm not sure how this is any different

---

### Post by ks07 on 2010-06-15
> **chrisccoulson said:**
> Hmmmm, there are plenty of tools that can "bork" the system when used improperly - eg, rm, dd, fsck, fdisk, mkfs etc. I'm not sure how this is any different
While this is true, isn't the OP talking about how using it correctly still breaks certain parts of the system?

Looking at this, this isn't a problem with usermod. Rather it's a problem with the large number of programs that use absolute paths (e.g. wine, like was previously said). Quite difficult/time consuming to fix properly. Just my 2 cents... :popcorn:

---

### Post by recluce on 2010-06-15
As ks07 stated: you will bork your system, even though you used usermod correctly and even repected the "caveat" in the man-page. Given this, I was proposing a few ways for a work-around and asked for comments.

I realize that a fix cannot be short-term (see "long term solution"), that is why I believe some work-around is necessary.

---

### Post by seeker5528 on 2010-06-17
> **recluce said:**
> Nobody cares for a tool included in Ubuntu that can totally bork the system? Somehow, the Lucid development forum was a bit more lively...

How was the system borked? You said it seemed to work fine initially?

Usually there is some configuration stuff that can be deleted, without having to go to the extreme of dumping the whole user account. K3B in particular doesn't save anything on it's first run that needs to be kept, so going into the .kde directory to look for the K3B stuff and deleting it is not a big deal. If you are going to extremes it is much easier to delete the '.gnome*', '.kde' and '.config/*', and other '.' directories instead of dumping the user account. 

As for wine, the registry stuff works like it does in windows, don't know that the wine developers can do anything to change that without breaking compatibility with windows software, so I think you are probably stuck with hard coded directory paths in the wine registry the same as you are in the windows registry.

I would agree that the man page/help should include some blurb about not moving/renaming home directories if the user account has been in use and you don't understand what the consequences associated with that are.

Later, Seeker

---

### Post by recluce on 2010-06-18
> **seeker5528 said:**
> How was the system borked? You said it seemed to work fine initially?


I wrote that it *appeared* to work fine at first. The "borkage" spread during regular use of the system, especially the GNOME problems. I did describe what happened in my first post, don't know what else to add.  


> 
Usually there is some configuration stuff that can be deleted, without having to go to the extreme of dumping the whole user account. K3B in particular doesn't save anything on it's first run that needs to be kept, so going into the .kde directory to look for the K3B stuff and deleting it is not a big deal. If you are going to extremes it is much easier to delete the '.gnome*', '.kde' and '.config/*', and other '.' directories instead of dumping the user account. 


You are probably right there, but at some point I lost confidence in the account, as even more trouble might have lurked beneath the surface. So I went to a somewhat more extreme solution to eradicate the problem. And yet, a few small items remain, even with the new account:

- There are still undeleteable items in "Applications > Other" of the GNOME menu

- The context menu "Open with other Application" brings up a ton of junk entries, usually WINE stuff that appears ten times or so

If anybody could give me an idea where to edit these menus "under the hood", I would really be thankful.


> 
As for wine, the registry stuff works like it does in windows, don't know that the wine developers can do anything to change that without breaking compatibility with windows software, so I think you are probably stuck with hard coded directory paths in the wine registry the same as you are in the windows registry.


I don't think that entries like "DesktopFile"="/home/stephan/.local/share/applications/wine-extension-chm.desktop" would be made by any Windows program, these have to be made by WINE. Typical windows entries also get "wrapped" (for lack of a better term) to refer to the equivalent path in the file system. These wraps and entries should be convertable to relative paths.


> 
I would agree that the man page/help should include some blurb about not moving/renaming home directories if the user account has been in use and you don't understand what the consequences associated with that are.


Yep - and there should be the confirmation request before executing the home directory rename. But since there has been hardly any reaction here, I suppose it would be moot to open a bug on launchpad. If the power-users here don't care, the even more empowered developers usually care less. So people will continue to bork their systems this way... :(

---

### Post by ranch hand on 2010-06-18
Power users.   I like that, thanks.

Back when I was using W98 I was a "power user" if that term can really be applied to a MS user.  I would like to get as good as I was on that with Linux.  This will take some doing as the bar, as I see it, is much higher.  I are a noob.  I are not fluent in geek even.

Testing seems to be a good learning environment though.

I think that most folks, instead of renaming an existing account would have created a new account, given the permissions to it to use the existing files, tested it, if fine deleted the old account.

This could very well be a very wrong approach.  Like I say, I are a noob.  It is what I would have done because the idea of messing with an existing account gives me the willies if it is more than adding/removing a permission or two.

---

### Post by seeker5528 on 2010-06-19
> **recluce said:**
> You are probably right there, but at some point I lost confidence in the account, as even more trouble might have lurked beneath the surface. So I went to a somewhat more extreme solution to eradicate the problem. And yet, a few small items remain, even with the new account:

- There are still undeleteable items in "Applications > Other" of the GNOME menu

These may be system wide things that the user can't delete, but if you uncheck the box next to them in the menu editor, that should cause them to be hidden.

- The context menu "Open with other Application" brings up a ton of junk entries, usually WINE stuff that appears ten times or so[/quote]

Don't know about the context menu, I'm not seeing that on my system. Okular shows up several times on the 'open with other application' part of the context menu when I right click on an HTML file, so maybe it depends on what windows applications you have installed and what mime associations they have in wine that may be relevant to a particular file type. I don't have any window applications installed on the computer I'm on at the moment, but if .desktop files are created so menu entries are created in the 'wine' section of the menu, these .desktop files are probably created in '~/.local/share/applications/', you could look at these .desktop files in a text editor to see if they have a 'MimeType=' line and if so what that line includes.

> I don't think that entries like "DesktopFile"="/home/stephan/.local/share/applications/wine-extension-chm.desktop" would be made by any Windows program, these have to be made by WINE. Typical windows entries also get "wrapped" (for lack of a better term) to refer to the equivalent path in the file system. These wraps and entries should be convertable to relative paths.

That as a single item may not be that big of a deal, the bigger issue would be all the stuff pointing to 'c:\windows\profiles\username\whatever'. That's not to say it couldn't or shouldn't be fixed, but I expect if it's going to be fixed through bugs file up stream instead of with Ubuntu.

> Yep - and there should be the confirmation request before executing the home directory rename. But since there has been hardly any reaction here, I suppose it would be moot to open a bug on launchpad. If the power-users here don't care, the even more empowered developers usually care less. So people will continue to bork their systems this way... :(

I expect the idea of adding a confirmation request probably isn't going to fly. Yes, if it was added, it would be easy enough to also provide a way to over ride it for those people using it in scripts, but if I google for usermod, I don't see a lot of complaints that suggest people are using that feature, or if they are they must be people that know what they are doing. If there are not a significant number of complaints, there is not much incentive for the developers to make a change that will break peoples scripts.

If I search using the terms 'usermod' and 'howto', there are a couple of things that basically regurgitate the usermod man page, but it seems more likely that if someone is searching for a way to change their user name, they will come across one of the pages that just tells how to use usermod to change the user name and says nothing about the option to move the home directory.

Filing a bug against usermod asking the wording in the description of the '-l' and '-m' options be changed to include a warning about potential breakage if the user account has been in use seems like the best bet.

It would be tempting to think it might be a [Paper Cut](https://wiki.ubuntu.com/PaperCut), but I highly doubt anything to do with usermod would be considered something "that the average user would encounter... " and so would fail the criteria for being considered.

In the bigger picture I do consider it bad practice for things to use '/home/username/whatever' instead of '~/whatever' or '$HOME/whatever', but maybe this is something that gets lost with the intention that things should be able to be cross platform and able to be compiled for Windows with as few code changes as possible. I'm not a developer so I can't really say.

Later, Seeker

---

### Post by recluce on 2010-06-20
> **seeker5528 said:**
> These may be system wide things that the user can't delete, but if you uncheck the box next to them in the menu editor, that should cause them to be hidden.

> 
- The context menu "Open with other Application" brings up a ton of junk entries, usually WINE stuff that appears ten times or so

Don't know about the context menu, I'm not seeing that on my system. Okular shows up several times on the 'open with other application' part of the context menu when I right click on an HTML file, so maybe it depends on what windows applications you have installed and what mime associations they have in wine that may be relevant to a particular file type. I don't have any window applications installed on the computer I'm on at the moment, but if .desktop files are created so menu entries are created in the 'wine' section of the menu, these .desktop files are probably created in '~/.local/share/applications/', you could look at these .desktop files in a text editor to see if they have a 'MimeType=' line and if so what that line includes.


Thanks for the pointer, I found that directory - but the files in there seem to be correct, so I am still hunting for these freak entries in the "Open with" menu...


> 
That as a single item may not be that big of a deal, the bigger issue would be all the stuff pointing to 'c:\windows\profiles\username\whatever'. That's not to say it couldn't or shouldn't be fixed, but I expect if it's going to be fixed through bugs file up stream instead of with Ubuntu.


I see that this could be a bigger problem, unless they replace all references to the username with something like $username, so that the username gets filled in when that data is requested. Would be really nice to see that at some point in time.

> 
I expect the idea of adding a confirmation request probably isn't going to fly. Yes, if it was added, it would be easy enough to also provide a way to over ride it for those people using it in scripts, but if I google for usermod, I don't see a lot of complaints that suggest people are using that feature, or if they are they must be people that know what they are doing. If there are not a significant number of complaints, there is not much incentive for the developers to make a change that will break peoples scripts.

If I search using the terms 'usermod' and 'howto', there are a couple of things that basically regurgitate the usermod man page, but it seems more likely that if someone is searching for a way to change their user name, they will come across one of the pages that just tells how to use usermod to change the user name and says nothing about the option to move the home directory.


True, scripting would be a problem.


> 
Filing a bug against usermod asking the wording in the description of the '-l' and '-m' options be changed to include a warning about potential breakage if the user account has been in use seems like the best bet.


OK, I agree. That is the least common denominator - and would help people like me, that *generally* know what they are doing, but did not expect that particular pitfall. I will check out launchpad and file a bug later. Once I have done that, I will post back in here.

> 
It would be tempting to think it might be a [Paper Cut](https://wiki.ubuntu.com/PaperCut), but I highly doubt anything to do with usermod would be considered something "that the average user would encounter... " and so would fail the criteria for being considered.


Agreed

> 
In the bigger picture I do consider it bad practice for things to use '/home/username/whatever' instead of '~/whatever' or '$HOME/whatever', but maybe this is something that gets lost with the intention that things should be able to be cross platform and able to be compiled for Windows with as few code changes as possible. I'm not a developer so I can't really say.


In the case of WINE that would be something to see, WINE for Windows :lolflag:

However, I believe the motivations are probably a lot simpler: plain old human laziness...

---

### Post by seeker5528 on 2010-06-21
> **recluce said:**
> However, I believe the motivations are probably a lot simpler: plain old human laziness...

I have a tendency to think that the developers just don't think about path variables outside of certain types of use cases. So situations where they need be '~' or '$HOME' but places where that is not typically expected to be an issue it gets overlooked.

I think typically it is unexpected that the user would change their home directory, this would more typically be something an administrator might do in the workplace most often probably as part of a migration from one machine to another, or it might be used by a backup program that has the option to back up individual user accounts and restore them with all their original settings and permissions.

Typically I would expect that home users either set things up new and copy the data they want to save, do a back up and restore what they want, or use the same home directories without renaming them.

If this stuff is not thought of from the beginning, it may not be easy to change it later, but it does seem like if programs inherit a path on first run, in which case it would get the expanded path in their own configuration file, it shouldn't be that hard to offer a 'reset' option then gets the new expanded path if the home directory has changed.

For KDE it's it may be something to bring up in the [KDE forum](http://forum.kde.org/) since it is the official forum for KDE and non-distribution specific, maybe some people there would have a better idea on how this stuff relates relative to the KDE stuff. 

Don't know of a similar forum for Gnome. 

Probably needs to be a more general discussion about how the path is handled, instead of a thread about usermod, maybe that would bring other people with different ideas into the discussion.

Later, Seeker

---

