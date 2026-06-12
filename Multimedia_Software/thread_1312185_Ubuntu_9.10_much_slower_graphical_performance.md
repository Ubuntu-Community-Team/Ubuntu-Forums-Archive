---
title: "Ubuntu 9.10 much slower graphical performance"
date: 2009-11-02
forum: Multimedia Software
---

### Post by pkchips on 2009-11-02
Hello all,

I noticed earlier today that my Ubuntu was running much slower than usual. Essentially I just want suggestions as to how to fix it.

Compiz plugins such as the window picker were stuttering, Opera web browser was almost (but not quite) unusable due to slowness, and I found that watching a video resulted in a lot of tearing.

Also, usually I find I can run many videos simultaneously and not suffer a performance hit, but during this episode I could only really run 1.

Using glxgears, I was getting around 80fps per 5 seconds, despite having a NVIDA Geforce Go 7900 GTX. I did various tests to ensure that acceleration was enabled, and it was. Then, I tried restarting the computer twice and using XP which is fine.

After turning the computer off and coming back to it after an hour or two, the desktop performance was back to normal. However, glxgears is giving me frame rates of around 300fps. In Ubuntu 9.04 I was getting at least 6000.

Furthermore, when I played Tales of Monkey Island through Wine, I found that the game wasn't running at full speed and the mouse was stuttering. In Ubuntu 9.04, the game ran at full speed and without any stuttering whatsoever.

If anyone has any suggestions as to what might be wrong, please let me know.

---

### Post by Miguel Angel Da Vila on 2009-11-02
I have the same issue with two Nvidia GeForce 9500 GT aranged as SLI, as a workaround open the Nvidia X Server Settings under System/Administration and then in the section "X Server Xvideo Settings" which is under X Screen 0, uncheck the Sync to VBlank checkbox. Also verify that the Sync to VBlank checkbox under OpenGL Settings is unchecked.
This problem seems to be related to a issue between the nvidia drivers and the linux kernel related to vertical sync, or may be a problem in Ubuntu related to detect the right vsync.
I hope this works for you.

---

### Post by pkchips on 2009-11-03
Wow, that's a lot faster. I'm getting almost 40,000 fps on glxgears, I used to get about 6000 on 9.04....

Thanks for your help, it's definitely fixed the problem. However, I don't think VSync is the cause of the problem.

On 9.04, with VSync I had around 6000 fps, but on 9.10 I get around 300. When I switch off VSync, it suddenly shoots up to 40,000 fps and that suggests to me that the VSync issue is separate to the problem we are experiencing. In other words, I think there is something else that's reduced my frame rate from 6000 to 300 between 9.04 and 9.10.

---

### Post by jaymzw on 2009-11-15
I had a similar problem with stuttering and inconsistent performance on glxgears and sdlmame.  For me, the problem was power management settings - the CPU frequency policy on the 'performance' power scheme by default is 'dynamic', which doesn't seem to co-operate well with games.  Setting this to 'performance' instead yields much better results.

I used kpowersave to tweak the power management settings.

sudo apt-get install kpowersave 

Here's a quick test.

1) Run kpowersave if it is not already running.  
2) Right-click on the plug icon that appears in your taskbar and select 'Set CPU frequency policy', then set it to 'Performance'.  
3) Then try running your game again.

To edit the power profile permanently:

1) Right-click on the plug icon that appears in your taskbar and select 'Configure kPowersave".
2) Click on the 'performance' power scheme.
3) Click on the 'CPU Frequency Policy' section.
4) Change dropdown value to 'Dynamic'.
5) Click 'apply' or 'ok'.

Seems like a bug in power management to me, on the dynamic setting the CPU should probably run on full tilt for a longer period of time...

---

### Post by gerowen on 2009-11-16
I'm using Gnome and the power management will affect performance.  I just installed sensors-applet, and then added a CPU meter for each core to my app bar and that way I can turn up the frequency settings when I want to.  By default it's set to "ondemand" which will cause things to stutter if you've got a lot going on.  I'm just using a laptop ATI-Radeon 3100 and with Compiz enabled I still get 6000 frames per 5 seconds using "on demand".  If I turn it up to "Performance" and max out both proc cores, it jumps up to just over 7k frames per 5 seconds.

---

