---
title: "Jaunty flash video issue...."
date: 2009-08-08
forum: Multimedia Software
---

### Post by evworld on 2009-08-08
Would someone please see it they can get a video to play on this site?

[http://www.philadelphiaeagles.com/index.html](http://www.philadelphiaeagles.com/index.html)


You should be able to click the play button on video.  Flash seems to work on other sites but not this one.  I really need it to work here....

---

### Post by HappyFeet on 2009-08-08
The link and video works for me. How did you install flash, and what version? Are you using the swfdec version?

---

### Post by evworld on 2009-08-08
I am not sure how I installed it.  I just installed Jaunty on my computer a few weeks ago. I belive I had a pop up from firefox and installed it that way.

 Youtube plays but not videos for the Eagles site.  The video just keeps trying to load, it never starts.

I am not sure what this means...   Are you using the swfdec version?

Thanks for the help..

---

### Post by HappyFeet on 2009-08-08
> **evworld said:**
> Are you using the swfdec version?


No. I am using the official adobe flash plugin. Go to synaptic and search for adobe flash and then do another search for swfdec, and then another one for flashplugin-nonfree. See what you have installed. Then report back. I'm sure I'll help you get it going. After all, we got to have those all important football videos. I'm a colts fan btw.

---

### Post by evworld on 2009-08-08
When I search adobe flash I have these two installed

Flashplugin-installer  10.0.32.18ubunto0
flashplugin-nonfree 10.0.32.18

When I search swfdec  I have nothing installed that the search results came up with.

---

### Post by HappyFeet on 2009-08-08
Let's try installing flash the way *I* have it. Go back to synaptic and *completely remove* flashplugin-nonfree. Then do:
```
sudo apt-get clean && sudo apt-get autoremove
```
Then go [here]("http://get.adobe.com/flashplayer/") and download the .tar.gz for linux flash file. Right click the file and choose "extract here". You will now have a **libflashplayer.so** file. Right click and copy it. Next go to your home folder and do Ctrl-H to show your hidden directories. Go to the .mozilla folder and open it. While inside the .mozilla folder, right click and choose "create folder". Name it **plugins**. Open plugins folder. Right click while in there and paste the libflashplayer.so file. Close home folder.

Open terminal again and do:
```
sudo apt-get install mozilla-mplayer
```
Restart firefox if open.

---

### Post by evworld on 2009-08-08
> **HappyFeet said:**
> Let's try installing flash the way *I* have it. Go back to synaptic and *completely remove* flashplugin-nonfree. Then do:
```
sudo apt-get clean && sudo apt-get autoremove
```Then go [here]("http://get.adobe.com/flashplayer/") and download the .tar.gz for linux flash file. Right click the file and choose "extract here". You will now have a **libflashplayer.so** file. Right click and copy it. Next go to your home folder and do Ctrl-H to show your hidden directories. Go to the .mozilla folder and open it. While inside the .mozilla folder, right click and choose "create folder". Name it **plugins**. Open plugins folder. Right click while in there and paste the libflashplayer.so file. Close home folder.

Open terminal again and do:
```
sudo apt-get install mozilla-mplayer
```Restart firefox if open.


Ok I did all that and I still cant play video.  It still keeps trying to load.  The instructions you gave me seemed to install but I still can't see videos off the Eagles site.  

When I go to tools > addons > plugins in firefox I don't see anything saying adobe flash. ??

---

### Post by HappyFeet on 2009-08-08
In firefox, type in **about: plugins** with no spaces.

You should see flash then.

---

### Post by HappyFeet on 2009-08-08
Check in synaptic to see if you have gnash installed. If you do, completely remove it. Regardless of that, do the following:

Go back to ~/.mozilla/plugins and remove the **libflashplayer.so** file. Then go back [here]("http://get.adobe.com/flashplayer/") and download the .deb for ubuntu 8.04+. Just click to install.

---

### Post by evworld on 2009-08-08
Sorry for being a newb, but how do I do.

Go back to ~/.mozilla/plugins and remove the **libflashplayer.so** file

Do I just delete the folder you had me make - plugins in mozilla.

---

### Post by HappyFeet on 2009-08-08
> **evworld said:**
> 

Do I just delete the folder you had me make - plugins in mozilla.

Yes.

---

### Post by NoVista on 2009-08-08
3 days ago flash seemed to have broke for some, but only on specific sites. I'd like to know if when you go to mlb.com, do you see flash working on the front page? The eagles site works fine here too on my desktop puter, but i bet if I had my laptop go there it would not, due to flash breaking on an update.

The flash mlb prob is brought up here:
[http://ubuntuforums.org/showthread.php?t=1231817](http://ubuntuforums.org/showthread.php?t=1231817)

I am curious to see how this turns out for you.

---

### Post by evworld on 2009-08-08
> **HappyFeet said:**
> Check in synaptic to see if you have gnash installed. If you do, completely remove it. Regardless of that, do the following:

Go back to ~/.mozilla/plugins and remove the **libflashplayer.so** file. Then go back [here]("http://get.adobe.com/flashplayer/") and download the .deb for ubuntu 8.04+. Just click to install.


It will not let me install that because I am running the 64 bit ubuntu version.

---

### Post by evworld on 2009-08-08
> **NoVista said:**
> 3 days ago flash seemed to have broke for some, but only on specific sites. I'd like to know if when you go to mlb.com, do you see flash working on the front page? The eagles site works fine here too on my desktop puter, but i bet if I had my laptop go there it would not, due to flash breaking on an update.

The flash mlb prob is brought up here:
[http://ubuntuforums.org/showthread.php?t=1231817](http://ubuntuforums.org/showthread.php?t=1231817)

I am curious to see how this turns out for you.


The mlb site does not work either....

---

### Post by HappyFeet on 2009-08-08
> **evworld said:**
> It will not let me install that because I am running the 64 bit ubuntu version.

AHA! You did not tell me you were using the 64bit version of ubuntu. (so am I) [Here]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz") is the 64bit libflashplayer.so (right click and extract)

Just put it in ~/.mozilla/plugins like you did before. Restart firefox. But first remove any flash you installed via a .deb file. (remove in synaptic)

It is important to let people know you are using 64bit ubuntu.

---

### Post by evworld on 2009-08-08
> **HappyFeet said:**
> AHA! You did not tell me you were using the 64bit version of ubuntu. (so am I) [Here]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz") is the 64bit libflashplayer.so (right click and extract)

Just put it in ~/.mozilla/plugins like you did before. Restart firefox. But first remove any flash you installed via a .deb file. (remove in synaptic)

It is important to let people know you are using 64bit ubuntu.


Thanks for your help so far.

I did the above.  I now have MLB working but no Eagles.  When I do the  about: plugins thing I don't see adobe flashplayer.  I see all kinds of media plugins.  Could I have two of the same type and firefox don't know which one to use.

Here a list of the bold plugins I see.

Shockwave Flash
Default Plugin
Demo Print
Iced Teave Java
VLC Multimedia
Windows Meda Player 10
Divx Web Player
Quicktime 7.2
Divx Browser
Qicktime 7.4
Real Player
Windows Media Player
Mplayer 3.55
Kaffine 

I don't know  the one Media player also show mplayer with it....

---

### Post by HappyFeet on 2009-08-08
Did you restart firefox?

Maybe the iced tea plugin has something to do with it. I use the sun-java6-plugin. Remove iced tea and try java. Also try the kiwi live cd I mentioned to see if the eagles site works.

---

