---
title: "Hardy Heron, Firefox 3b5, and Java plugin"
date: 2008-05-03
forum: Multimedia Software
---

### Post by marvinlee on 2008-05-03
I've noticed tons of people reporting issues with HH 8.04, Firefox3, and the Java plugin(s). I'm a bit of a newb with Linux, but this is what worked for me. I use Logmein for my work and it's what I used to test the java plugin. 
  What happened previously with Logmein was, when I did a remote connection to a computer, I could see the desktop, but every click just refreshed the whole screen.
  I currently have Java6, with the browser plug-in installed. I also had the gcjwebplugin. All I did was go into synaptic and uninstall the gcjwebplugin and logmein worked again. Also, the "dancing duke" plugin tester on the java website working correctly (showing correct info and recognized as installed), where before I could see the dancing dude but it said java wasn't installed. I've read a lot about the icedtea plugin, but I've never had that installed to my knowledge. 
   Like I said, I'm pretty new to this stuff, so I'll check this thread periodically to see if anyone has any questions about my setup that might be relevant but I don't know about. 
  Other than that, my upgrade from Gutsy was smooth as silk!

---

### Post by FrodeA on 2008-05-09
Thanks a lot, that did the trick for me:)

It seems that the icedtea-plug in is the culprit. After upgrading to Hardy Heron, I was not able to load Java-aplets to my bank account, rather awkward in the long run... The same problem occured using 7.10 when I tried icedtea, had to uninstall to make my Java work correctly. Didn't realize it was installed until I read your reply.

---

### Post by cor2y on 2008-05-09
The iced-tea plugin has improved esp with the update to OpenJDK (the opensource version of Java) so its no different from the closed source version/plugin, the only thing is visit the java site to check your version and the open source version is like .2 or .3 versions behind the closed source version.
OpenJDK and the iced-tea plugin works with all java apps or web pages.

---

### Post by FrodeA on 2008-05-09
I'm not a Linux-expert, just a common user, so I can't say whether the plugin has improved or not. All I can say, is that both with Gutsy Gibbon and Hardy Heron my Java-pages worked in general on most pages, but not on encrypted ones (e.g. pages belonging to financial services). To enable Java on these encrypted (https with SSL) pages, I had to disable/uninstall the iced-tea plugin. I haven't checked if this has been reported as a bug, but is this a possibility?

:confused:

---

### Post by carusoswi on 2008-07-08
> **marvinlee said:**
> I've noticed tons of people reporting issues with HH 8.04, Firefox3, and the Java plugin(s). I'm a bit of a newb with Linux, but this is what worked for me. I use Logmein for my work and it's what I used to test the java plugin. 
  What happened previously with Logmein was, when I did a remote connection to a computer, I could see the desktop, but every click just refreshed the whole screen.
  I currently have Java6, with the browser plug-in installed. I also had the gcjwebplugin. All I did was go into synaptic and uninstall the gcjwebplugin and logmein worked again. Also, the "dancing duke" plugin tester on the java website working correctly (showing correct info and recognized as installed), where before I could see the dancing dude but it said java wasn't installed. I've read a lot about the icedtea plugin, but I've never had that installed to my knowledge. 
   Like I said, I'm pretty new to this stuff, so I'll check this thread periodically to see if anyone has any questions about my setup that might be relevant but I don't know about. 
  Other than that, my upgrade from Gutsy was smooth as silk!

Well, I'm here to tell you, ever since upgrading to 7.10, Java 6 has never behaved with my system and Logmein.  The last time I was able to use it was when downgrading Java to version 5.  Since upgrading to 8.04, no joy for me whatsoever.  I've had to rely upon XP to do my remote computing to my office.

That, while annoying, would have been such a problem except that, often during the week when I'm away from home, I rely upon whatever wireless connections I can find.  It seems that XP has a terrible time with weak wireless connections.  Ubuntu seems reluctant to connect to new connections for some reason, but, if I use XP to establish a relationship between the weak connection and my wireless adapter, then Ubuntu, for some reason, will readily connect and seems unencumbered by the weakness of the signal . . . I don't worry about figuring it out, I just do what I need to in order to use it.

In the meantime, not being able to get Logmein working with Ubuntu meant that I could not really use that application when away from my home workstation because XP would drop my wireless connection so often that it was not practical to use XP with Logmein away from home. 

Thank you so much for pointing out IceTea as the culprit.  I uninstalled that plugin and have spent the last hour or so remotely reviewing and printing architectural drawings at my office from my home . . . exactly what the doctor ordered for me.

Thanks again.  How the heck did you figure this out.  I've been asking and searching for a long time now for an answer to this little problem.

Caruso

---

### Post by carusoswi on 2008-07-08
It's just so cool that Logmein and Ubuntu are working again.  One less reason to boot into Xp for me.

Sorry to be redundant, but, THANKS AGAIN!

Caruso

---

### Post by carusoswi on 2008-07-09
One quick question, then, I'll stop bothering you on this -- what is the IcedTea plugin?  I don't even remember installing it.  What does it do?

Caruso

---

### Post by p252 on 2008-07-09
OpenJDK does not work on encrypted java applets. I suspect the problem may be with the icedtea plugin it uses. I uninstalled the icedtea plugin and install sun-java6 with it's plugin. Now I can get the java web applet to start but soon after Firefox (3.0) just crashes. It crashes every time. This is really annoying since I'm using Ubuntu for work and most of our web login/applications are secure java applets.

---

### Post by jamesstansell on 2008-07-09
> **carusoswi said:**
> One quick question, then, I'll stop bothering you on this -- what is the IcedTea plugin?  I don't even remember installing it.  What does it do?

Caruso

The history of the icedtea plugin is something like this.  If anyone knows better I'm happy for corrections.

 * Sun released most of the source code for Java 7 as OpenJDK (alpha status)
 * The IcedTea project was formed to fill in some of the holes for the code that Sun didn't release (generally used bits from the Classpath project)
 * Sun release OpenJDK6, which had the alpha changes taken out so that it is functionally equivalent to Java 6
 * The IcedTea6 project was formed to fill in the bits missing from OpenJDK6
 * The languishing gcjwebplugin and netx projects were tapped to provide a functional plugin for the IcedTea projects
 * for hardy, ubuntu switched to openjdk-6-jre and icedtea-gcjwebplugin as the default java providers.  These are both from the icedtea6 project, as I understand it

The icedtea plugin has 2 big holes that are responsible for most of the issues people are seeing.
 1. No livescript bridge for Java <--> Javascript connections
 2. No support for trusting a signed applet

Those are being worked on, but it's a work in progress.  Probably not even worth calling alpha status yet.

For anyone running a 64-bit ubuntu, there is no sun-java6-plugin available, so icedtea-gcjwebplugin is the only 64-bit option.  If that doesn't work there may be a variety of options for using Sun's 32bit plugin.  Your personal situation and preference will determine how 'clunky' those options are though.

---

### Post by carusoswi on 2008-07-09
Ok, thanks, James.  I read your answer, but have to admit it doesn't mean much to me.  I reckon, then, that IcedTea is a code name for developments in Java.  I very much depend upon Logmein to function and much prefer to work in Ubuntu as opposed XP, so, since stumbling onto this thread, I am a much happier (if not much better informed) camper.

Caruso

---

### Post by YogiPaolo on 2008-07-28
I do not have IcedTea installed, but logmein still does not work for me. 

I'm running Hardy on 64 bit.

I'm not sure exactly what packages I'm supposed to need to make java applets work, but the dancing duke fella moves jerkily across my screen. I have java6 installed, but the site says I'm using java5.

I've seen reference to a package called:  sun-java6-plugin but searching for it using apt-cache and synaptic yields nothing. Do I need this package? I also have the java console extension in firefox.

When I declare java in logmein, i get nothing but a gray screen.

---

