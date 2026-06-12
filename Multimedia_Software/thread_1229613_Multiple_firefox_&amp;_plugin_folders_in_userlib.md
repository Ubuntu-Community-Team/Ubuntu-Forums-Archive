---
title: "Multiple firefox &amp; plugin folders in user/lib"
date: 2009-08-02
forum: Multimedia Software
---

### Post by paks.dreamer on 2009-08-02
Hi guys, this is my first real question so I hope I've posted in the right place.  I'm pretty new to using linux, specifically ubuntu, and I've succeeded in setting up most things the way I'd like without a problem.  However I'm still a baby to this OS, and I came across something really confusing today, when trying to manually add a plugin to my firefox when it didn't install itself properly.

I installed the adobe flash player into my system, but the** libflashplayer.so** (adobe flash player plugin -- the one I'd like to use), didn't go into a correct, working firefox folder, but into a folder named **adobe-flashplugin** only, which seems to do nothing to help my firefox.  I thought, that's easy, I can just copy or extract it across to my firefox folder so it will work.

Here's where I came across the confusing thing.

In my **user/lib** folder I have* four different folders for firefox!!*, each with different files and settings within:

- **firefox** contains **/plugins**/flashplugin-alternative.so, libjavaplugin.so, only two plugins of the eight my firefox currently has enabled.

- **firefox-3.0.12** contains many folders such as **/chrome, /components, /defaults, /dictionaries, /distribution, /extensions, etc, etc** and seems to be my main firefox folder with all my profile and settings, however the **/plugins** folder is empty!

- **mozilla** contains **/plugins**/flashplugin-alternative.so, libjavaplugin.so, libtotem-cone-plugin.so, libtotem-gmp-plugin.so, libtotem-mully-plugin.so, libtotem-narrowspace-plugin.so, and a folder named **/extensions** (empty) and seems to be where my firefox is reading its working plugins from.. though again it doesn't seem to display all eight plugins, other plugins I have enabled in firefox at current are QuickTime Plug-in, VLC Multimedia Plugin, etc.. at least it seems that way to me!

- **mozilla-firefox** contains **/plugins** (empty)

My question is which folder is the real one that my firefox is using, and is it safe for me to delete the other folder/s, and am I right in assuming that I can extract the plugin I actually want (libflashplayer.so) to one of these folders and have it actually work in my firefox?

Perhaps I need to disable some old versions of firefox or delete them altogether, and somehow merge the settings & plugins I want into the one place?  It just seems such a mess all over the place, with extra folders doing nothing, plugins I have enabled which can't be found, and plugins I can find but aren't available in firefox.

I hope this makes sense.  Thanks in advance for any help. :]

*[SIZE=1]~Paks.[/SIZE]*

---

### Post by grizzler on 2009-08-02
Yes, it is a mess and no, you don't want to go and delete things until you know exactly what you're doing. It's quite possible one or more of the folders is a left over from a previous version and at least one is a kind of 'generic' pointer to the current version, but I'm not making a guess as to what is what (mainly because I'm using a manually installed Firefox 3.5.1 which makes things different yet again).
If you really, *really, **really*** want to clean up the mess now, the only 'safe' way I can think of is to remove Firefox **completely** (using Synaptic), then remove anything related to it you may find left in **/etc** and **/usr/lib** (be careful not to remove too much...) and then install Firefox again.
Oh, and you might want to look at any existing **xulrunner** folders as well, because they're part of Firefox too (no, that's not a joke - well i.m.o. it is, sort of, but not *that* way...). You may find your 'missing' plugins there.

To make matters worse, this particular plugin needs to be in yet another folder, which you apparently haven't discovered yet... :)

Don't let the mess confuse you. Just follow these steps. That's what I did and it worked for me.

1. Remove/disable any current flash plugin from Firefox's Add-ons/Plug-ins window.

2. You say you're new to Linux. Are you aware of hidden folders/files? Open your home folder in Nautilus. Do you see any folder or file names starting with a dot? Great. Those are the hidden ones. Otherwise press ctrl+h and you should see them.

3. Open the hidden folder **.mozilla** in your home folder. It should contain a folder called **firefox** and there may be one called **plugins**. If there isn't, create one.

4. Copy the **libflashplayer.so** file from wherever you've seen it into **~/.mozilla/plugins** (in case you don't know this yet: the tilde is short for **/home/<your username>**)

5. Restart Firefox and check the Add-ons/Plug-ins window. The Shockwave Flash plugin (10.0 r32) should be there.

Hope this helps.

By the way, I think there's definitely something wrong with this plugin's installation procedure. I've seen several postings about it on this forum (and others).

There's a lot more to say about the multiple Firefox folders and their contents (actually, some of the files you've mentioned are probably softlinks rather than files...). I don't like the mess either. It reminds me too much of Windows with its twelve or more Application Data folders. I have actually done what I mentioned at the start of this post, i.e. removed the lot, after I had put my Firefox in /opt. But it did require some 'study' and I must admit that I didn't make notes on what I removed.

---

### Post by paks.dreamer on 2009-08-02
Cheers grizzler, that helps a lot.  I thought I might have to do something like that; it's a shame to hear it will still be a bit messy, but at least it's somewhat of a planned mess that I can minimise. :>

---

