---
title: "libpipelight-flash.so : Firefox now using Windows version of Flash through Wine?"
date: 2014-06-15
forum: Multimedia Software
---

### Post by jonathanfv on 2014-06-15
Hi people. I'd like to have some clarifications. Yesterday, I updated my computer, and I noticed that the update seemed to install a Windows version of Flash through Wine. At first, I didn't think anything about it, because I thougt that one of my Wine programs might have needed it. But today, I noticed that Flash behaved a little bit differently than usual, and discovered that Firefox is now using a Windows version of Flash. Firefox still has the Flash 11.2 plugin, and both the 11.x and the 13.x are activated. I thought that I could deactivate one of them to choose which one I want to use at a certain time, but if I deactivate one, they both get deactivated, and if I activate one, they both get activated.

It bugs me. I don't like that Flash was installed through Wine in Firefox without my consent, and even thought Flash is usable on most sites, for some applications, it is absolutely not. Per example, if I want Flash to access my microphone, well, it won't work through Wine. I do have the Windows version of Firefox and Flash installed in Wine, and I tested it out of curiosity, and it didn't work. That's one thing that really bugs me. I know that Flash is no longer being supported in Linux, and updates will not be provided, but that's something that should be up to the user to decide what to do. If I remember correctly, I had to install Flash when I set up my system because it only came as an option in the repositories, or I had to download it from Adobe or something. I'm not sure anymore. But the point is, why would an update change the version of Flash I installed for a Windows version of Flash through Wine? I think it's going a little bit far. And not only that, but the version that was provided to me via the update of the repository isn't even the latest one, and it's got vulnerabilities! I don't want outdated Windows crap installed on my computer without being warned and given the choice. Man, on Windows they have version 14. Why the hell did I get version 13?

I know this thread is starting to look like a rant, but I'm really, really not happy about that update.

Edit: I really don't mean to trash the Pipelight team, they seem to have done a really good job. I just really hate that I was not given a choice.

---

### Post by jonathanfv on 2014-06-15
So, my question is, how do I remove it? I don't know how to remove the plugin from Firefox and keep the native plugin. I tried Galternatives, but it doesn't seem to add the option of ligthpipe. I removed lightpipe-multi, but Firefox still seems to be using Flash 13. So did I get hacked or something? How would Firefox have started using Pipelight and Flash for Windows without me doing anything in that regard, and then still keep doing that even when I make sure Pipelight isn't installed? Makes no sense to me!

Edit: I restarted my computer after having uninstalled Netflix Desktop, Pipelight, Flash. Reinstalled the native Flash, and the Windows version of Flash is gone. My remaining question is: was Pipelight part of the system update I just did? Because when I saw the plugin and looked in Synaptic, I couldn't find any mention of it, and I had to manually install the repository to see it. Do people have any idea how it might have landed on my computer? That's what is worrying me. I didn't do it, I know I didn't. I couldn't find the package in Synaptic, so where the hell did it come from?

---

### Post by monkeybrain20122 on 2014-06-15
You must have enabled pipelight flash yourself at some point. You don't need to remove pipelight

To disable flash
```
sudo pipelight-plugin --disable flash
```

(need sudo only if you have enabled it with sudo, otherwise you can leave it out. But if not sure, run the command twice, with and without sudo)
To enable it
```
pipelight-plugin --enable flash
```

It used to be that you always leave it enabled and you switch between it and flash 11.2 with update-alternatives (or galternatives as you said, though it is broken in 14.04 [https://bugs.launchpad.net/ubuntu/+source/galternatives/+bug/1309709](https://bugs.launchpad.net/ubuntu/+source/galternatives/+bug/1309709), see stinkeye's work around)

but since 0.2.7 they changed something, if pipelight flash is enabled, then automatically Firefox would use the higher version (i.e. pipelight). 

To switch you can either use pipelight-plugin --enable/disable as above, or, always keep pipelight-flash disabled (run pipelight-plugin --disable flash once and forget about it) and then use galternatives to switch.

See [https://answers.launchpad.net/pipelight/+question/249841](https://answers.launchpad.net/pipelight/+question/249841)

---

