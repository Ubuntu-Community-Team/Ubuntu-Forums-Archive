---
title: "Classic: Moving the menus back"
date: 2011-03-18
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Dzugavili on 2011-03-18
I would like to put the menus back on the windows and put Places and Settings back to their spots on the menubar.

It should be noted that I can't find anything in Compiz or Appearance for this setting. And Google doesn't work, it's just people bitching about how the menu bar was moved.

Reasons the menu update doesn't work:
* moving my mouse up to the menu takes more time and effort than moving it to the top of the window I'm using.
* 22" 1080p screens don't have a shortage of space for menu bars.
* having to open just one more menu to get to the menus I *actually* use seems less ergonomic, not more.

Reasons it should work, but doesn't on a desktop:
* If you're on a 10 inch netbook screen, you might need the space.

P.S. -- Unity is terrible.

Edit:
Unity is making me really cranky.

Edit:
This isn't a post about Unity. The post-script is about Unity. And the edits.

---

### Post by wormyblackburny on 2011-03-18
Hence why you are given the option to use the traditional Gnome desktop. I pray to god that doesn't go away. I agree. Unity is garbage, or maybe I am just stuck in my ways......  You don't see Windows or Mac completely re-tooling the user experience (or most Linux flavors for that matter). Lets not re-invent the wheel when there is no need.

---

### Post by Dzugavili on 2011-03-18
Traditional Gnome seems to have the menu hack added also.

I want to turn that off.

Edit:
*"You don't see Windows or Mac completely re-tooling the user experience  (or most Linux flavors for that matter). Lets not re-invent the wheel  when there is no need."*
Well, to some extent Windows Vista and 7 worked it over and OS X was a complete retool (I didn't even touch anything between 7.6 and X, so I'm not entirely sure).
But yes, this is the clear problem. The computer interface as it exists now is fairly well tuned and doesn't need much changing.

In fact, the addition of the dock seems to be pandering to the Mac community. As someone who runs way too many windows, docks don't work for me; I need the text to identify just what I have open.

---

### Post by mc4man on 2011-03-19
Well - Classic uses gnome-panel, gnome-panel uses applets
remove what you don't want, add what you do.

---

### Post by Dzugavili on 2011-03-19
Okay, status update:

Firefox no longer has a menu showing up top either. Not really sure how I'm going to get to my bookmarks, if I had any.

All other windows seem to be working though.

Edit:
[I]"remove what you don't want, add what you do."
[/I]A valid point. Except:
- The menus being moved from the windows to the upper menu bar isn't an applet. In fact, this behavior explicitly counter-indicates the function I need.
- Places and Settings don't appear to be on my "Add to Panel" menu, I can't add them.
- Drawer is not a substitute; doesn't have the same behavior.

Edit:
The Gnome menu bar applet seems to add it, but it breaks the menu functionality. Testing in post below...

---

### Post by cariboo on 2011-03-19
Have you tried removing firefox-globalmenu?

---

### Post by Dzugavili on 2011-03-19
Trying now:

Incidentally, there is an applet for the Places and System, I apologize for that one.
Unfortunately, I think it just completely broke the menu bar. It's not showing for any program now...

 Let me reboot Firefox, see if anything changes...

Edit:
Removing firefox-globalmenu did the trick -- for Firefox. Please tell me they rebuilt DLL hell by making such a package for every single application.

Various issues:
* If you remove the Main Menu panel button, there is no way to put it back. I got a grey square there now.
* You can't move the old style Menu into the new style's place.
* It seems with enough tweaking, the menu bar at the top just breaks.
* I could really use a menu for showing what's in my bar right now...

 **S****OLUTION**:

Okay, bare with me:

DELETE YOUR TOP PANEL

There seems to something in there that isn't available from the 'add' menu that seems to move the menu bars up to the top.
It seems toying with the original is a lot more work than just wiping it oujt.
By deleting the top panel, I seem to have returned menus to each of my others.
I had to rebuild it, but that was effortless.

There is an panel item called "Indicator Applet Appmenu", which looks like how to restore it, but the applet crashes before it'll show up.
<edit2> No, that is it. But it seems to kind of buggy until you reboot; the menus don't pop off the windows until you click them (the menus), and even then it doesn't seem to put the menu at the top. Just File -> Close. 
And it appears to be built from something else, judging by the About text.</edit2>

I'm happy so far.

---

### Post by mc4man on 2011-03-19
> "remove what you don't want, add what you do."
A valid point. Except:
- The menus being moved from the windows to the upper menu bar isn't an applet. In fact, this behavior explicitly counter-indicates the function I need.
- Places and Settings don't appear to be on my "Add to Panel" menu, I can't add them.
- Drawer is not a substitute; doesn't have the same behavior.

I don't use Classic - booted into it, took about 20 sec. to make it just like maverick - the so called 'global menu' is an applet, you just r. click on - unlock, then r. click -  remove,  add the menu bar back, stick a firefox icon,  ect.

Edit; this was a fresh install, nothing changed, modded, or deleted - so a log in back to unity, same 3 apps, all still w/ global menu ect.
(the profiles for Desktop (unity) and Classic are separate and be be set up differently

---

### Post by Dzugavili on 2011-03-19
Couldn't tell you why I was having so many problems then. The thing wasn't responding to right clicks; maybe I had to hit an edge or something.
Though, it certainly seems like I did something strange up in that corner. It got pretty broken for a second.

Thankfully, I can't even put it back. I'll leave that one for someone else though.

Edit:
I was having issues with Unity not showing up the first couple of boots; plus, it's ugly as all hell. 
I'm still having Compiz crash out every hour or so, but that's manageable, it gives a retry menu.

ATI or nVIDEA? I have an HD 5750, which I think might be to blame for some of the issues I had with Unity.
I don't think the ATIs/AMDs are running 3d out of the box just yet, or at least they aren't recognized first boot.

---

### Post by standards on 2011-04-05
> **mc4man said:**
> the so called 'global menu' is an applet, you just r. click on - unlock, then r. click -  remove

i just spent an ungodly amount of time trying to figure this out and thought the many, many, thousands of people who are probably also pulling their hair out over this may be interested in how to get rid of this garbage as well, so here it is. thank you mc4man!

---

