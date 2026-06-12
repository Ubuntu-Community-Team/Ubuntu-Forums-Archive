---
title: "Flash stop working"
date: 2012-01-18
forum: Multimedia Software
---

### Post by goldie4042 on 2012-01-18
Has anyone ever experienced a problem with flash like the picture attached to this post. It seems as though I started experiencing this problem after an update earlier today. My browsers will not play any flash video. And I say browsers because this problem is happening with Chronium and Firefox. Any help or guidance will be greatly appreciated.

---

### Post by wolfen69 on 2012-01-18
Remove flash then go [here]("http://get.adobe.com/flashplayer/") and download the .tar.gz flash file. Right click and *extract here*. Then take the resulting *libflashplayer.so* and put it in ~/.mozilla/plugins (go to your home folder and do Ctrl-H, and that will show you your hidden folders. Go to the .mozilla folder and create the plugins folder, and put the libflashplayer.so in there) Restart firefox.

---

### Post by goldie4042 on 2012-01-19
Thanks Wolfen. I actually got it to work again. I read a couple of articles on google telling me how to uninstall flash. So I uninstalled and reinstalled and it started working again. For anyone else that has this problem try this first.

sudo apt-get remove flashplugin-installer
sudo apt-get install flashplugin-installer



I assume that some settings got changed when I updated my system because I did not get the "flash plugin needs to be installed"message or any other error message. The only message or error that I was receiving was the picture above when trying to play flash video.

---

