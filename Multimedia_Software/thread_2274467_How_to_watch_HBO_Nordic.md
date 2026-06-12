---
title: "How to watch HBO Nordic"
date: 2015-04-20
forum: Multimedia Software
---

### Post by Lubu123 on 2015-04-20
HBO Nordic is not officially supporting Linux but it does work at least with Firefox on Lubuntu 14.04 and Linux Mint (17.1 and 17.2). When I first tried the service on Lubuntu I had some problems though: when choosing a film the loading icon appeared but nothing happened. At the moment HBO Nordic needs both flash and widevine enabled in the browser in order to work.

I had flash installed by flashplugin-installer (which may have caused the problem) and widevine by pipelight. The solution in my case seemed to be to get rid of old flash plugin by uninstalling flashplugin-installer package and enabling pipelight's flash plugin. I also had to clear Firefox plugin cache with pipelight.

So here's how to make HBO Nordic work with Firefox - **works with Netflix too**:

**1. Close Firefox**

**2. Install Pipelight**
```
sudo add-apt-repository ppa:pipelight/stable
sudo apt-get update
sudo apt-get install --install-recommends pipelight-multi
sudo pipelight-plugin --update

```
[http://pipelight.net/cms/install/installation-ubuntu.html](http://pipelight.net/cms/install/installation-ubuntu.html)

**3. As a precaution you may want to get rid of the old flash version** by uninstalling flashplugin-installer (Lubuntu) or adobe-flashplugin (Linux Mint) if you have one installed
```
sudo apt-get remove flashplugin-installer
```
OR
```
sudo apt-get remove adobe-flashplugin
```

**4. Enable Pipelight's flash and widevine** (you may also want to enable silverlight since although it is not required for HBO, Netflix and many other similar services use it)
```
sudo pipelight-plugin --enable flash
sudo pipelight-plugin --enable widevine
sudo pipelight-plugin --enable silverlight

```
[http://pipelight.net/cms/installation.html#section_2](http://pipelight.net/cms/installation.html#section_2)

**5. Update plugins and clear Firefox plugin cache** like this:
```
sudo pipelight-plugin --update
sudo pipelight-plugin --create-mozilla-plugins

```
 [http://pipelight.net/cms/faqs/faq-pipelight-error-in-aboutplugins.html](http://pipelight.net/cms/faqs/faq-pipelight-error-in-aboutplugins.html)

**6. Start Firefox and let Pipelight install its plugins** - there will be installation messages on the screen and when they disappear restart Firefox. You should now see the newly installed Pipelight plugins in Firefox plugins tab.

**7. Install [User Agent Overrider]("https://addons.mozilla.org/en-Us/firefox/addon/user-agent-overrider/") addon for Firefox and select the profile "Firefox/Windows"** so that your browser appears as a Windows browser (otherwise HBO and some other similar services may complain about you having an incompatible operating system or they might just simply not work)
[SIZE=1]EDIT 8-2015: it seems that HBO Nordic has updated the service since now I can use it without User Agent Overrider enabled
EDIT 11-2015: Netflix on the other hand needs to believe that you are using the service with Windows so you should enable UAO in that case[/SIZE]

[HR][/HR]
[SIZE=1]Note: If you encounter problems, close Firefox and repeat step 5
Note2: It may not always be necessary to uninstall the old flash version (see [this reply]("http://ubuntuforums.org/showthread.php?t=2274467&p=13346475#post13346475")), but like said earlier the old flash *seemed* to cause a problem on Lubuntu 14.04. Uninstall the old flash plugin, test, reinstall and test again so you will know.
At least on Linux Mint 17.2 both flash versions can be active on Firefox without any problem.
Note3: There are plenty of user agent switcher addons but all of them may not work in this context as User Agent Overrider does
Note4: You may also want to update the Firefox version number in the User Agent Overrider settings every now and then because some websites may complain about an old browser version.[/SIZE]

---

### Post by Said Bak on 2015-05-20
Great How-To - Netflix now works for me in Firefox on Ubuntu 14.04 (it didn't before). However for HBO Nordic I still get this error message:

> HBO Nordic requires that Adobe Flash is installed in order to watch content. [Install now]("http://get.adobe.com/flashplayer/").

Does this mean I'll have to re-install ```
flashplugin-installer
```?

---

### Post by jose85 on 2015-08-26
I'm new to Linux and followed the steps above, but it still does not work.  How do I go about uninstalling everything that was just installed?

---

### Post by Lubu123 on 2015-08-28
Said Bak, when I have had the error you describe I have been able to solve it by closing Firefox and repeating step 5.

---

### Post by Lubu123 on 2015-08-28
> **jose85 said:**
> I'm new to Linux and followed the steps above, but it still does not work.  How do I go about uninstalling everything that was just installed?

Can you see the plugins in Firefox plugin tab? Maybe you should close Firefox, type
```
sudo pipelight-plugin --create-mozilla-plugins
```
and start Firefox to see if the plugins are there.


Anyway, if you still wish to uninstall, to remove pipelight and configuration files:
```
sudo apt-get purge pipelight-multi
```

... and to remove the repository:
```
sudo add-apt-repository -r ppa:pipelight/stable
```

---

### Post by monkeybrain20122 on 2015-08-28
Why do you remove flashplugin-installer? If you enable pipelight flash then it would automatically be used because FF always chooses the highest version, but there are times you may want to use native flash because it does tend to work better when both works (or sometimes pipelight flash doesn't work for things like menus and buttons or sites where players use foreign fonts) In those cases you may want to disable pipelight flash (pipelight-plugin --disable flash) and let 11.2 take over.

Also, hal probably works.

---

### Post by Lubu123 on 2015-08-28
> **monkeybrain20122 said:**
> Why do you remove flashplugin-installer? If you enable pipelight flash then it would automatically be used because FF always chooses the highest version, but there are times you may want to use native flash because it does tend to work better when both works (or sometimes pipelight flash doesn't work for things like menus and buttons or sites where players use foreign fonts) In those cases you may want to disable pipelight flash (pipelight-plugin --disable flash) and let 11.2 take over.

Also, hal probably works.

Good point. It seemed a problem to have the two plugins in the system - at least some time ago on Lubuntu. On the other hand, I don't think the native flash plugin has ever been a problem on Linux Mint.

---

### Post by Jaguarandine on 2016-03-22
Hi, I've been trying to use this method to watch HBO Go in the US. Unless the video is full screen, I get a black screen and only audio. When I do change it to full screen, video and audio usually work, but playback controls disappear, there may be some video corruption, and oftentimes I cannot exit full screen without killing flash. Also, the video quality isn't that good. I guess it's better than nothing, but am I the only one having this problem? Thanks.

---

### Post by Jaguarandine on 2016-03-28
Does no one have this problem? Or maybe I should create a new thread?

---

### Post by QIII on 2016-03-28
Hijacking an old thread marked as solved is a sure way to have your question overlooked.

Please start a new thread.

Closed.

---

