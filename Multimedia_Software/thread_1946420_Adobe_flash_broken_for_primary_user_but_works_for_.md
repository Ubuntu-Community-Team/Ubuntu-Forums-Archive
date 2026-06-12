---
title: "Adobe flash broken for primary user but works for newly created user"
date: 2012-03-24
forum: Multimedia Software
---

### Post by promet on 2012-03-24
Hello,

I've recently had my Adobe Flash Plugin:

File:  /usr/lib/firefox-addons/plugins/libflashplayer.soVersion:   Shockwave Flash 11.1 r102(installed via Flash-Aid in Firefox)


stop working for me. It will play audio through the course of a flash video, then, once the audio completes, will play choppy video afterward, if at all. 



I'd read some posts where trying flash by creating a new user account was a possible troubleshooting step. I've created a new user and the plugin works perfectly for that newly created user. Though I would, of course, like it to work for my primary account as well. 



Apparently my primary user has got some mucked up account settings or something interfering with the plugin's operation. Please let me know if anyone has any thoughts on this, and thanks!

---

### Post by wildmanne39 on 2012-03-24
Hi, in the primary account open firefox clixk on tools>addons then type flashaid into the search box and install it and follow the directions it will fix almost all flash issues for the whole computer not just firefox.
Thanks

---

### Post by promet on 2012-03-25
> **wildmanne39 said:**
> Hi, in the primary account open firefox clixk on tools>addons then type flashaid into the search box and install it and follow the directions it will fix almost all flash issues for the whole computer not just firefox.
Thanks

Hey [wildmanne39]("http://ubuntuforums.org/member.php?u=508533"),

I'd been using Flash-Aid, quite successfully, up until this problem occurred, I should have mentioned that, and after the problem occurred I've uninstalled and reinstalled Flash through the Flash-Aid addon in all of the various options since, none of which, sadly, has worked. Again though, it runs like a charm in the separate, newly created user. Go figure...

I really appreciate your taking the time to reply though. Please let me know if you've got any other ideas.

Thanks!

---

### Post by garvinrick4 on 2012-03-25
##If all else fails remove all remnants of flash and install new from Adobe.
# "Stopping any Firefox that might be running"
sudo killall -9 firefox

# "Removing any other flash plugin previously installed one at a time:"

sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper

sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rf /usr/lib/nspluginwrapper


Download flash from adobe to Downloads
cd Downloads
tar zxvf libflashplayer-(version of flash).so.tar.gz 
sudo cp libflashplayer.so /usr/lib/mozilla/plugins/

---

### Post by promet on 2012-03-25
Hey Garvinrick4,

I followed your instructions. It's worth noting though, that I got the following when trying to remove flashplugin-nonfree and libflashsupport:

```
Virtual packages like 'flashplugin-nonfree' can't be removed
Virtual packages like 'libflashsupport' can't be removed
```Turns out, that didn't present a problem though, the others had already been removed during my frenzy to try and fix this issue before, EXCEPT, that is, nspluginwrapper; the only package, in my case, that actually was removed by your above commands.

As of now everything is working great again=D>. So, I am going to chalk this up to an unnecessary and or corrupted version of nspluginwrapper ruining the party, not to mention robbing a good chunk of CPU cycles during the time it was running.

Thanks a million for taking the time to help me out, I really appreciate it.

Moving this one to the "SOLVED" pile.

Cheers

---

### Post by garvinrick4 on 2012-03-25
> I followed your instructions. It's worth noting though, that I got the  following when trying to remove flashplugin-nonfree and libflashsupport:Hi promet,
 The instructions were just to remove anything and everything that can be removed some
of course are not installed. But when new guys used to try to install flash stuff would be everywhere so I used this then, 
overkill but worked. Nowadays Lovinglinux's flash-aid scripts
usually removes all the junk then reinstalls do not know why it did not work for you or why
just one user flash did not work. For some reason I got used to downloading my own flash
from adobe when they had beta 64 bit not in Ubuntu repo's. Anyway good to keep this just in case it always works. 
I actually got this from an old bash script and tore it apart and made it manual.  Have a nice day promet.

---

