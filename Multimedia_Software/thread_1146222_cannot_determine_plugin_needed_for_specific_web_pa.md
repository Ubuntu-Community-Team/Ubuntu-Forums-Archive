---
title: "cannot determine plugin needed for specific web page"
date: 2009-05-02
forum: Multimedia Software
---

### Post by zero7404 on 2009-05-02
running the latest firefox (3.0.10) in 8.10, but i can't determine the plugin i need to have installed in order to get certain pages to display properly....

for example, i frequently go here and set my clocks with the correct time:

[http://www.time.gov/](http://www.time.gov/)

when i select my region, the time display does not come up as it normally does in windows' firefox....

how do i determine which plugin i need when i run into this ? with some pages i can right click on the media window and in properties i see Totem as the plugin, but the media won't play....

---

### Post by gandaran on 2009-05-02
> **zero7404 said:**
> running the latest firefox (3.0.10) in 8.10, but i can't determine the plugin i need to have installed in order to get certain pages to display properly....

for example, i frequently go here and set my clocks with the correct time:

[http://www.time.gov/](http://www.time.gov/)

when i select my region, the time display does not come up as it normally does in windows' firefox....

how do i determine which plugin i need when i run into this ? with some pages i can right click on the media window and in properties i see Totem as the plugin, but the media won't play....
do you have java installed? if not install the java plugin, look in synaptic for sun-java6-plugin check for install and hit apply.

---

### Post by zero7404 on 2009-05-02
i noticed there was a popup for some program to use the /tmp folder for cache, but i thought that was an ad, it kind of looked like one...so i'd just close it. i do have java installed...

i tried it again and said OK, then the clock came up...

i forgot the name of the plugin requesting the cache folder, started with an N and had an X in the name...

---

### Post by bobince on 2009-05-02
Incidentally you don't need Java or any other plugin to use time.gov. Just shave the “java” off the end of the URL and it'll give you a non-updating version where you can read the time as normal text. eg. [http://time.gov/timezone.cgi?UTC/s/0](http://time.gov/timezone.cgi?UTC/s/0)

Personally I'd avoid Java unless there's a particular site/applet you definitely need to use that relies on it. The more browser plugins you have installed, the bigger your browser's attack surface. (See the current wave of attacks against Windows users through the Adobe Reader plugin.)

---

### Post by zero7404 on 2009-05-02
bobince, i'm pretty careful about the sites i visit, most of the time i go to the web pages i've bookmarked, so i'm not too worried about browser attacks at the moment.

i've installed the web of trust (WOT) plugin for firefox and it warns me when visiting shady web pages....

---

### Post by bobince on 2009-05-03
> **zero7404 said:**
> i'm pretty careful about the sites i visit

That's not the defence it once was. Mainstream sites (and sites they depend on such as advertisers) are being hacked all the time, resulting in iframes to exploits being silently inserted onto the page.

(For example, an advertiser on foxnews.com was serving up PDF exploits for several days a week or so ago. Even the vBulletin software this site uses has had some serious content-injection security holes in the past.)

---

