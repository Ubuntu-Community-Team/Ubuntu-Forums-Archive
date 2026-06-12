---
title: "Adobe Flash Installer"
date: 2010-01-11
forum: Multimedia Software
---

### Post by anechoic on 2010-01-11
OK so I've had this problem with Flash content that I was too lazy to resolve:
I couldn't play back certain flash content at all
some YouTube, no Vimeo, and other content also seldom if ever worked
not a problem since most of this stuff is a time soak anyway
but I got to the point where I needed to view some content for work
and I grew tired of pulling out my Apple Powerbook to view this content

so I committed the bandwidth to solving this and it was not that hard
here is a step by step of my process of discovery and solution that might be of some help for others in the same boat:

- load up some known Flash content in Firefox
- [http://vimeo.com/](http://vimeo.com/) is a good site for Flash rich content that didn't work on my Linux laptop
- click little blue lego icon in bottom bar
- up comes a dialog box titled 'Manage Content Plug-ins'
  - click on 'Plug-ins in use' if not already selected

[in my case I had Gnash in service to handle Flash content - which is not a very reliable plug to use]

- click on the plug in listed in the dialog box - a pull down menu will show
- go to 'Search'
- a window should appear titled 'Plugin Finder Service'
[in my case I had:
-- Swfdec SWF player
-- Adobe Flash Player (installer)
-- Gnash SWF Player
listed]

- I selected the Adobe Flash Player (installer) but each time I attempted to install it via the little wizard app in this Plugin Finder Service window it would appear to install but then not show in the list when I went to switch the plugin used in the 'Manage Content Plugins' box

- The problem was that the Adobe installer was putting the plug-in in the wrong place so I instantiated a root window:
(this could just as easily have been done in a terminal)

sudo nautilus

entered my root password
navigated  
/usr/lib/flashplugin-installer

found the file
'libflashplayer.so'

opened another tab and typed in:
/usr/lib/mozilla/plugins

went back to the other tab and dragged the 
'libflashplayer.so' file into the mozilla plugins directory

- restarted Firefox
- navigated to a Flash rich page like boingboing
- clicked on little blue lego at bottom of window

went through the procedure above again 
   (i.e. Search in pull down menu etc etc)
but this time you should see a listing for 'Adobe Flash Player (installer)'
selected next in the wizard and follow the procedure until the end

- selected blue lego icon again 
- went to the pull down
- selected Adobe Flash PLayer (installer)
- closed window

now see if the content on Vimeo and other sites such as boingboing.net
work in your browser

OK -- not sure I have all the steps listed clearly but essentially the
problem is that Adobe puts the plugin in the wrong place and you have to
move it and point Firefox to it

hope this helps someone!
:)

---

