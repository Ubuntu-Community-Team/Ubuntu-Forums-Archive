---
title: "How can I update 'restricted extras' in Lubuntu? (especially Flash Player plugin)"
date: 2013-10-20
forum: Multimedia Software
---

### Post by LubLearner on 2013-10-20
Hi

I cannot find restricted-extras package for Lubuntu in Lubuntu software. The Ubuntu, Kubuntu and Xubuntu restricted extras are there, so I am afraid of there not being Lubuntu restricted extras nowadays. Before upgrading to Lubuntu 13.10, I installed Flash Player plugin for Chromium and now Firefox tells me that this plugin and a Quicktime plugin are out of date despite the fact that Lubuntu software updating says there are not any updates for the system.

How can I keep updated these plugins? I think I might check in Firefox if Flash Player plugin is out of date in order to update it with Chromium, because I cannot open its apt link from Firefox, but is not there a better way to do that? The Quicktime plugin is a worse problem cause I click on updating the plugin in Firefox and I get to an Apple webpage without any downloads. Is this plugin really necessary? May I uninstall it and use Firefox normally?

---

### Post by howefield on 2013-10-20
Try this thread..

[http://ubuntuforums.org/showthread.php?t=2009173](http://ubuntuforums.org/showthread.php?t=2009173)

---

### Post by Dennis N on 2013-10-20
You should be getting the latest available version of flash for your release through your normal updates. You should see flashplugin-installer installed in your system which takes care of flash updates (if any) for you.

To see your version:

```
dn@Zotac:~$ apt-cache policy flashplugin-installer 
flashplugin-installer:
  Installed: 11.2.202.310ubuntu0.12.10.1
  Candidate: 11.2.202.310ubuntu0.12.10.1

```
or use Firefox Add-ons manager to see the version.

Version is 11.2.202.310

(This output is on 12.10.)

Quicktime: My Firefox 24.0 doesn't have a quicktime plugin, and I haven't missed it.

---

### Post by LubLearner on 2013-10-20
Hi

You are right. Flash Player Plugin is updated. Although Firefox does not say that, the installed version is the same as the Adobe website one. I cannot understand why this happens. May it be related to the Adobe policy for Linux? I have just read they are only publishing security updates, but this browser is a version made specially for Ubuntu systems, should not it notice this?

The other plugins I said is also updated. Firefox calls it QuickTime Plug-in 7.6.9, but it is "Gecko Media Player 1.0.8 Plug-in for QuickTime, RealPlayer and Media Player streams using MPlayer" according to its description. There is a link toward Gecko Media Player website and this is the lastest version. This must be a similar problem.


I had forgotten to look for lubuntu-restricted-extras package in Synaptics Package Manager, but I am not sure if I will installed it as I know now the plugins are updated. Firefox plays the online videos better than Google Chrome and Chromium before upgrading to Lubuntu 13.10 and better than Windows XP browsers too, so I prefer not doing many changes.


I will mark the threat as solved.

---

