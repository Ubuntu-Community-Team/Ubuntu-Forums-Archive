---
title: "Radiotray icon fail to launch"
date: 2011-04-25
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by dino99 on 2011-04-25
i've installed this nice app on natty i386, this program start without error logged but the icon, which is where you can really select and start listening radio, never appear into the taskbar as it should.
Googling around i cant find how is called this icon. This issue is with the "classic" desktop, its the same with maverick, it only works with lucid on my end.

---

### Post by macstevejb on 2011-04-25
To make these items appear, as they do in 10.10 in the notification area, whitelist them as follows:

The default whitelist can be displayed via 
gsettings get com.canonical.Unity.Panel systray-whitelist

To whitelist another application
gsettings set com.canonical.Unity.Panel systray-whitelist "['JavaEmbeddedFrame', 'Wine', 'Skype', '<application name here>']"

Or simply whitelist everything
gsettings set com.canonical.Unity.Panel systray-whitelist "['all']"

I have radiotray working perfectly in 11.04 running Unity.

HTH

regards :D

---

### Post by dino99 on 2011-04-25
thanks for the tip, but the problem is without compiz/unity, eg classic

---

### Post by rodeh on 2011-04-25
for compatibility with natty and the new indicator system you need to manually change the config so that radiotray will launch the application indicator rather than try to launch the tray icon. 

        gedit ~/.local/share/radiotray/config.xml

update these lines, changing "false" to "true":
  <option name="enable_application_indicator_support" value="true"/>
  <option name="enable_application_indicator_theme_support" value="true"/>

then save and restart radiotray.

If you want radiotray to start automatically when you log in, don't forget to add it to your startup applications. 



hope this helps.

---

### Post by dino99 on 2011-04-26
thanks,

i've made the config change but still dont get that icon

/usr/bin/radiotray output:

Loading configuration...
/home/oem/.local/share/radiotray/bookmarks.xml
/home/oem/.local/share/radiotray/config.xml
PLS playlist decoder
M3U playlist decoder
ASX-familiy playlist decoder
XSPF playlist decoder
ASF playlist decoder
RAM playlist decoder
Using url timeout = 2000

if i check the radiotray process properties, i see:
/usr/bin/python  (pointing to python2.7)
/usr/bin/radiotray

---

### Post by rodeh on 2011-04-26
Did you install from the repositories or did you download the latest .deb from the developers website? here >  [URL="http://radiotray.sourceforge.net/"]http://radiotray.sourceforge.net/
[/URL]

---

### Post by dino99 on 2011-04-26
> **rodeh said:**
> Did you install from the repositories or did you download the latest .deb from the developers website? here >  [URL="http://radiotray.sourceforge.net/"]http://radiotray.sourceforge.net/
[/URL]

both cases tested on maverick and natty i386, same result, only works on lucid

---

### Post by rodeh on 2011-04-27
Have you tried adding the Notification Area back to the panel? (right click > 'Add to Panel') (the config changes I posted earlier would need to be reverted to 'False' for the icon to appear)

Have you tried running radiotray with the config changes in Unity?

You might need to restart your session for changes to take effect.

Beyond this I'm pretty much a noob...

---

### Post by mdurham on 2011-04-27
maybe [this thread]("http://ubuntuforums.org/showthread.php?t=1733540") has some explanation

---

### Post by dino99 on 2011-04-27
> **rodeh said:**
> Have you tried adding the Notification Area back to the panel? (right click > 'Add to Panel') (the config changes I posted earlier would need to be reverted to 'False' for the icon to appear)

Have you tried running radiotray with the config changes in Unity?

You might need to restart your session for changes to take effect.

Beyond this I'm pretty much a noob...

hm you are a skilled noob :)
you have pointed the good thing:
- adding the "notification area" do the trick: that damn icon popup, and i get my fav radio :)
- i've not reverted the previous changes (false ->true): dont seems very important

So going to comment my bug report now :)

---

### Post by rodeh on 2011-04-27
Glad it's working dino99, although I don't understand why the application indicator is not showing. This was implemented to comply with the new application indicator standard in Ubuntu, but retain backword compatibility. It works fine for me on both settings.

Have a look at what the default config.xml says, maybe the user config.xml in your home folder is being ignored for some reason

gedit /usr/share/radiotray/config.xml

You could always try changing the lines in here to 'true' (using sudo gedit to open the file this time of course) and see if that works, if so it may be a permissions issue or something. (Don't forget to change it back if it doesn't work!)

The idea is that you no longer need to use the notification area: [http://design.canonical.com/2010/04/notification-area/](http://design.canonical.com/2010/04/notification-area/)

btw here's what the config looks like in my home folder (~/.local/share/radiotray/config.xml) :
```
<config>
  <option name="enabled_notifications" value="true"/>
  <option name="volume_increment" value="0.05"/>
  <option name="volume_level" value="0.5"/>
  <option name="url_timeout" value="100"/>
  <option name="enable_application_indicator_support" value="true"/>
  <option name="enable_application_indicator_theme_support" value="true"/>
<option name="sleep_timer" value="15"/><option name="last_station" value="Radio Reddit"/></config>
```and here's what the default looks like (/usr/share/radiotray/config.xml) :
```
<config>
  <option name="enabled_notifications" value="true"/>
  <option name="volume_increment" value="0.05"/>
  <option name="volume_level" value="1.0"/>
  <option name="url_timeout" value="100"/>
  <option name="enable_application_indicator_support" value="false"/>
  <option name="enable_application_indicator_theme_support" value="false"/>
</config>
```And the application indicator (rather than notification icon) appears ok.

---

