---
title: "Flash 9 crashes,fails to integrate with jsp"
date: 2007-01-26
forum: Multimedia &amp; Video
---

### Post by nimy on 2007-01-26
Flash 9 plays well but it causes my browser to crash randomly on certain links (not Flash ones, but others, can't see a method to it).  It also fails to integrate with jsp extensions, a major issue for me because I'm taking online courses that require it.

I've browsed through the posts in this forum and there doesn't appear to be a solution :(  
I had no problems with Flash 7 on Breezy or Hoary, however I lost the Flash 7 .xpt and .so files when I installed Flash 9.  I've tried to recover Flash 7 somewhere but all I could find were Debian warnings that this is not recommended.  

I tried removing the Totem etc plugins to make sure that they weren't conflicting with Flash 9, and after removing the packages the only plugin that remains is Realplayer audio (nphelix.so), which I doubt would cause a conflict.  

So should I re-install Flash 7 and if so, where can I find a stable version?

---

### Post by RomeReactor on 2007-01-26
Looks like you don't have java. Open a terminal and write:

```
sudo apt-get install sun-java5-jre sun-java5-plugin
```

Then, still on the terminal, write:

```
firefox
```

and see if the pages load. If they don't, look at what the terminal outputs and post it here.

---

### Post by nimy on 2007-01-27
sorry, forgot to mention that I have  libjavaplugin_oji.so
  for  Java(TM) Plug-in 1.5.0_06, with the plugins that go with it: x-java-vm plus associated java applets and beans.  So when I type 'firefox' at the prompt, a browser window is launched  - I assume that's the default behavior,  If x-java-vm &#8800; sun-java5, let me know and I will install as you recommend.

---

### Post by RomeReactor on 2007-01-27
You haven't yet mentioned if you're on Firefox, Epiphany, Opera or another browser; anyway, it looks like this is all my java library. To install it:

```
 sudo apt-get install java-common libcommons-net-java libhsqldb-java libjaxp1.2-java libjline-java liboro-java libservlet2.3-java libxalan2-java libxerces2-java libxt-java openoffice.org-java-common sun-java5-bin sun-java5-fonts sun-java5-jre sun-java5-plugin
```

To see if you're missing something. This setup lets Firefox handle java pretty well. Might as well try to install all of these and see if it works for you...

---

### Post by nimy on 2007-01-27
I'm using Firefox 1.5 - "About Firefox" shows this:
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.0.9) Gecko/20070126 Ubuntu/breezy-security Firefox/1.5.0.9

I tried installing the java modules per your recommendation and got some errors - some modules were not found and there was an error in the open-office java plugin so that wasn't installed, but that module is non-essential anyway.  After restarting my browser there's no change in behavior - macromedia flash 9 videos still load correctly with sound, but the jsp page I'm trying to access still shows up blank.  I don't know if my browser will crash soon, but I was happy not to lose this thread when I checked my favorite Flash9 website. 

I checked "about:plugins" in my browser window before and after the java module installs and there's no change in the list.  This is what it shows:

Java(TM) Plug-in 1.5.0_06-b05

    File name: libjavaplugin_oji.so
    Java(TM) Plug-in 1.5.0_06

MIME Type 	Description 	Suffixes 	Enabled
application/x-java-vm 	          Java 		 Yes
application/x-java-applet 	Java 		Yes
application/x-java-applet;version=1.1 	         Java 		 Yes
application/x-java-applet;version=1.1.1 	Java 		Yes
application/x-java-applet;version=1.1.2 	Java 		Yes
application/x-java-applet;version=1.1.3 	Java 		Yes
application/x-java-applet;version=1.2 	          Java 		  Yes
application/x-java-applet;version=1.2.1 	Java 		Yes
application/x-java-applet;version=1.2.2 	Java 		Yes
application/x-java-applet;version=1.3 	          Java 		  Yes
application/x-java-applet;version=1.3.1 	Java 		Yes
application/x-java-applet;version=1.4 	          Java 		  Yes
application/x-java-applet;version=1.4.1 	Java 		Yes
application/x-java-applet;version=1.4.2 	Java 		Yes
application/x-java-applet;version=1.5 	          Java 		  Yes
application/x-java-applet;jpi-version=1.5.0_06 	Java 	   Yes
application/x-java-bean 	                               Java 	       Yes
application/x-java-bean;version=1.1 	           Java 	   Yes
application/x-java-bean;version=1.1.1 	Java 		Yes
application/x-java-bean;version=1.1.2 	Java 		Yes
application/x-java-bean;version=1.1.3 	Java 		Yes
application/x-java-bean;version=1.2 	 Java 		  Yes
application/x-java-bean;version=1.2.1 	Java 		Yes
application/x-java-bean;version=1.2.2 	Java 		Yes
application/x-java-bean;version=1.3 	 Java 		  Yes
application/x-java-bean;version=1.3.1 	Java 		Yes
application/x-java-bean;version=1.4 	  Java 		  Yes
application/x-java-bean;version=1.4.1 	Java 		Yes
application/x-java-bean;version=1.4.2 	Java 		Yes
application/x-java-bean;version=1.5 	  Java 		  Yes
application/x-java-bean;jpi-version=1.5.0_06 	Java  Yes

---

### Post by nimy on 2007-02-10
Flash 9 has been running for some time on my Ubuntu client without browser crashes, and even though CISCO's jsp pages don't work as they used to, I can still access Redhat's jsp pages from here.  Given CISCO's lack of compatibility with *nix clients, it's not surprising that the pages I need don't work.  

In addition to the answers here, I found the following Ubuntu page helpful:
[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/java.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/java.html)
and to a lesser extent, this one:
[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/web-browsing.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/web-browsing.html)

Thanks :)

---

