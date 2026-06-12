---
title: "Plugins in Firefox - how to choose?"
date: 2007-02-17
forum: Multimedia &amp; Video
---

### Post by jewellc on 2007-02-17
Hi all,

I have a question concerning plugins for Firefox in Edgy.  I have totem,  mplayer, and helix installed.  I spend far too much of my time listening to the BBC Radio 3 website ([www.bbc.co.uk/radio3)](www.bbc.co.uk/radio3)), and would like to specifically use the Helix plugin for the audio (as the site is designed for this).  However, whenever I go to the site, Firefox tries to use the Totem plugin, which barfs at the ra feed.  If I then click on the "Use standalone Real Player" link, the MPlayer plugin starts up!

Is there a way to get Firefox to specifically use the Helix plugin for realaudio without having to uninstall the other plugins?

Thanks,

Chris

---

### Post by meng on 2007-02-17
I advise you "quaranitine" the totem plugins, in the terminal do the following:
cd /usr/lib/mozilla-firefox/plugins
sudo mkdir quarantine
sudo mv libtotem* quarantine

and restart firefox

Clearly, this can be easily undone if you change your mind at a future date.

EDIT: to remove the propensity of mplayer to chime in, then you need to go further and add
sudo mv mplayerplug-in-rm* quarantine

(this will leave the other mplayer plugins intact)

---

### Post by marmux on 2007-02-20
I just happened to find out another way to do the job, which in my opinion is cleaner.
The problem is that Firefox contains a lot of Download Actions that do not appear in the Download Actions Manager in Firefox preferences. For some strange reason, by default an action is listed there only if it is associated to a file type AND a file extension, but NOT to a file type alone. Most actions are associated only to file types with no extension specified, and so there is no control on them.
In order to change this behavior:
1) Type [COLOR="Blue"]about:config[/COLOR] in the address bar
2) look for the option [COLOR="Blue"]browser.download.hide_plugins_without_extensions[/COLOR]
3) Change its value from true (default) to false by double clicking on it
4) Go to [COLOR="Blue"]Edit -> Preferences -> Downloads[/COLOR] and click on the [COLOR="Blue"]View and edit actions [/COLOR]button (in Firefox 1.5), or go to [COLOR="Blue"]Edit -> Preferences -> Contents[/COLOR] and click on the [COLOR="Blue"]Manage[/COLOR] button (in Firefox 2.0, if I remember correctly). The complete list will now appear
5) customize to your needs the action related to realaudio by clicking on the [COLOR="Blue"]Change Action[/COLOR] button.
This worked for me. I finally got rid of the annoying Adobe Reader plugin...

---

### Post by mr_ed on 2007-05-30
Oh thank you thank you.  I would feel my blood pressure rise when I visited that screen and found that I couldn't edit an action... and now I can see them all.  Thanks!  :)

---

### Post by ronocdh on 2007-05-31
> **marmux said:**
> I just happened to find out another way to do the job, which in my opinion is cleaner.
The problem is that Firefox contains a lot of Download Actions that do not appear in the Download Actions Manager in Firefox preferences. For some strange reason, by default an action is listed there only if it is associated to a file type AND a file extension, but NOT to a file type alone. Most actions are associated only to file types with no extension specified, and so there is no control on them.
In order to change this behavior:
1) Type [COLOR="Blue"]about:config[/COLOR] in the address bar
2) look for the option [COLOR="Blue"]browser.download.hide_plugins_without_extensions[/COLOR]
3) Change its value from true (default) to false by double clicking on it
4) Go to [COLOR="Blue"]Edit -> Preferences -> Downloads[/COLOR] and click on the [COLOR="Blue"]View and edit actions [/COLOR]button (in Firefox 1.5), or go to [COLOR="Blue"]Edit -> Preferences -> Contents[/COLOR] and click on the [COLOR="Blue"]Manage[/COLOR] button (in Firefox 2.0, if I remember correctly). The complete list will now appear
5) customize to your needs the action related to realaudio by clicking on the [COLOR="Blue"]Change Action[/COLOR] button.
This worked for me. I finally got rid of the annoying Adobe Reader plugin...
This is a great post. Bumping so a few more eyes get to see it!

---

### Post by kerry_s on 2007-05-31
could have just used the media player connectivty extension.
[https://addons.mozilla.org/en-US/firefox/addon/446](https://addons.mozilla.org/en-US/firefox/addon/446)

---

### Post by tomjennings on 2007-06-05
> **marmux said:**
> I just happened to find out another way to do the job, which in my opinion is cleaner.
...




Thanks 1E6!!! I *knew* there had to be a way to see those annoying invisible associations! Sheesh! Why do they even hide that stuff?

---

