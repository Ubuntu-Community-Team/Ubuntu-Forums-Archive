---
title: "Use Google Chrome's built-in Flash Player in Firefox? Please confirm."
date: 2013-03-31
forum: Multimedia Software
---

### Post by argonvegell on 2013-03-31
I found this while searching through Google, here's the url: 
[http://www.webupd8.org/2011/03/use-google-chrome-built-in-flash-in.html](http://www.webupd8.org/2011/03/use-google-chrome-built-in-flash-in.html)

> 
Use Google Chrome Built-In Flash In Firefox For (Probably) Less Crashes

I had some issues with Adobe Flash crashing very often using the latest Firefox 4 so I've searched for a way to fix this and found a topic on AskUbuntu which says to use Chrome's Flash plugin in Chromium so I though - why not do it for Firefox? - and it's actually working quite well for now.

Chrome uses a built-in Adobe Flash plugin which seems to work better then the regular Flash. But there's a catch: you must install Chrome (and keep it updated if you want further Flash updates) even if you don't use it.

Use the built-in Chrome Flash plugin in Firefox

1. Download and install Google Chrome (I for one prefer the unstable branch but I guess any version will do)

2. Open a terminal and copy / paste the following commands:

mkdir -p ~/.mozilla/plugins
ln -s /opt/google/chrome/libgcflashplayer.so ~/.mozilla/plugins/

3. Restart Firefox.

The exact same instructions above also work for Chromium (yes, using the ~/.mozilla/plugins/ folder even though it's for Chromium).

Note: I've tested this with the latest Firefox 4 32bit only (and Chromium 32bit)! It should work with older Firefox versions too though.


Please confirm this, thanks.

---

### Post by vasa1 on 2013-04-01
That is quite an old link. It talks about Firefox 4. Browsers have been evolving rather rapidly. At this time, Google Chrome uses Pepper Flash which is not compatible with any version of Firefox.

---

### Post by Yellow Pasque on 2013-04-01
It won't work with modern versions of the Google Flash plugin (> 11.2) because they only use Pepper/PPAPI plugin architecture and FF doesn't support it: [http://blogs.adobe.com/flashplayer/2012/02/adobe-and-google-partnering-for-flash-player-on-linux.html](http://blogs.adobe.com/flashplayer/2012/02/adobe-and-google-partnering-for-flash-player-on-linux.html)

---

### Post by argonvegell on 2013-04-01
> **vasa1 said:**
> That is quite an old link. It talks about Firefox 4. Browsers have been evolving rather rapidly. At this time, Google Chrome uses Pepper Flash which is not compatible with any version of Firefox. > **Temüjin said:**
> It won't work with modern versions of the Google Flash plugin (> 11.2) because they only use Pepper/PPAPI plugin architecture and FF doesn't support it: [http://blogs.adobe.com/flashplayer/2012/02/adobe-and-google-partnering-for-flash-player-on-linux.html](http://blogs.adobe.com/flashplayer/2012/02/adobe-and-google-partnering-for-flash-player-on-linux.html)  But what about with Chromium?

---

### Post by Yellow Pasque on 2013-04-01
This is a hack, but it could work: [http://www.ubuntuvibes.com/2012/07/how-to-install-latest-flash-player-in.html](http://www.ubuntuvibes.com/2012/07/how-to-install-latest-flash-player-in.html)

---

### Post by vasa1 on 2013-04-01
> **argonvegell said:**
> But what about with Chromium?
Nope. Chromium uses the "exact same" Flash that Firefox uses. Chromium doesn't use Pepper Flash. Pepper Flash is limited to Google Chrome.

---

### Post by argonvegell on 2013-04-03
> **Temüjin said:**
> This is a hack, but it could work: [http://www.ubuntuvibes.com/2012/07/how-to-install-latest-flash-player-in.html](http://www.ubuntuvibes.com/2012/07/how-to-install-latest-flash-player-in.html)  Thanks for the reply. I installed and tried Chromium today, it sucked completely, I got a headache setting it up, settings and such, Firefox is way easier to use, so I won't be using Google Chrome or Chromium anytime soon.  Anyway, I heard Firefox has a project ongoing, Shumway, so I'm hopeful that would replace Adobe Flash Player for Linux users who are loyal to Firefox.  I have some questions on Shumway, would it be able to play Facebook games created by Zynga and King.com? Like Candy Crush Saga, Chefville, CityVille?

---

### Post by vasa1 on 2013-04-03
> **argonvegell said:**
> ... I have some questions on Shumway, would it be able to play Facebook games created by Zynga and King.com? Like Candy Crush Saga, Chefville, CityVille?
Why don't you start a new, appropriately named thread? Something with *Shumway* in the title?

---

### Post by zika on 2013-06-25
> **vasa1 said:**
> Nope. Chromium uses the "exact same" Flash that Firefox uses. Chromium doesn't use Pepper Flash. Pepper Flash is limited to Google Chrome.Serendipity led me to this thread... Just to report that I'm writing this from Chromium using Pepper... Using it for quite some time...

---

### Post by vasa1 on 2013-06-25
> **zika said:**
> Serendipity led me to this thread... Just to report that I'm writing this from Chromium using Pepper... Using it for quite some time...
So?
It still doesn't change the fact that Chromium doesn't come with Pepper Flash. One has to take additional steps (like also downloading Chrome in order to point Chromium to the Pepper Flash.)

---

### Post by zika on 2013-06-26
> **vasa1 said:**
> So?
It still doesn't change the fact that Chromium doesn't come with Pepper Flash. One has to take additional steps (like also downloading Chrome in order to point Chromium to the Pepper Flash.)
Did I say it comes?
I'm not shy of taking additional steps...

---

### Post by TheKid965 on 2013-06-27
I don't have the page anymore where I got these steps, but this is all I needed to do to get Pepper installed in Chromium (Ubuntu 13.04):

*sudo add-apt-repository ppa:skunk/pepper-flash*
*sudo apt-get update && sudo apt-get install pepflashplugin-installer*

After that, I added the following line to **/etc/chromium-browser/default**, following the [FONT=Courier New]CHROMIUM_FLAGS=""[/FONT] line:

[font=Courier New]. /usr/lib/pepflashplugin-installer/pepflashplayer.sh[/font]

Restart Chromium, and it's running the latest Pepper Flash.  Didn't even need to install Chrome proper.

---

### Post by zika on 2013-06-27
> **TheKid965 said:**
> I don't have the page anymore where I got these steps, but this is all I needed to do to get Pepper installed in Chromium (Ubuntu 13.04):

*sudo add-apt-repository ppa:skunk/pepper-flash*
*sudo apt-get update && sudo apt-get install pepflashplugin-installer*

After that, I added the following line to **/etc/chromium-browser/default**, following the [FONT=Courier New]CHROMIUM_FLAGS=""[/FONT] line:

[FONT=Courier New]. /usr/lib/pepflashplugin-installer/pepflashplayer.sh[/FONT]

Restart Chromium, and it's running the latest Pepper Flash.  Didn't even need to install Chrome proper.
Yeap. That is one possibility...
I use other since I do not have either GoogleChrome or Chromium installed in ususal way...
Google is not present, I just extract PepperFlash&manifest.json (latter to know the version of flash-plugin...)
I extract latest (not older than 12 hours) Chromium and just let it know where the plugin is and what is its version, using command-line switches... Easily done and makeshift as it could be... No traces on system and easily maintained...
OK, back to U+1... It's been nice here... :lolflag:

---

