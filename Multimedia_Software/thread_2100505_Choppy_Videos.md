---
title: "Choppy Videos"
date: 2013-01-01
forum: Multimedia Software
---

### Post by bman on 2013-01-01
I have searched but haven't seen anything about it, not exactly.

I am running Ubuntu 12.04 and have Chrome 23.0.1271.97 installed. Not sure if it matters, but I have the default AMD drivers installed as well. When viewing videos on Youtube (that is all I have tested) the videos play fine, but if I move my mouse, the video is choppy, unwatchable.

Seems like it kinda gets worse as the video goes on as well.

Anyone else with this problem, any fixes?

---

### Post by xc3RnbFO8P on 2013-01-02
> **bman said:**
> I have searched but haven't seen anything about it, not exactly.

I am running Ubuntu 12.04 and have Chrome 23.0.1271.97 installed. Not sure if it matters, but I have the default AMD drivers installed as well. When viewing videos on Youtube (that is all I have tested) the videos play fine, but if I move my mouse, the video is choppy, unwatchable.

Seems like it kinda gets worse as the video goes on as well.

Anyone else with this problem, any fixes?

Did you try Chromium or Firefox?
show the output of
> lspci |grep VGA
and
> free

---

### Post by bman on 2013-01-02
No, because I don't want to use those browsers. I know that sounds stupid, but I should be able to use the one I want :)

```
03:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Cypress [Radeon HD 5800 Series]

```

```
             total       used       free     shared    buffers     cached
Mem:       8177352    8010796     166556          0      63248    4713784
-/+ buffers/cache:    3233764    4943588
Swap:      8385532      23964    8361568
```

---

### Post by xc3RnbFO8P on 2013-01-02
> **bman said:**
> No, because I don't want to use those browsers. I know that sounds stupid, but I should be able to use the one I want :)

```
03:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Cypress [Radeon HD 5800 Series]

```

```
             total       used       free     shared    buffers     cached
Mem:       8177352    8010796     166556          0      63248    4713784
-/+ buffers/cache:    3233764    4943588
Swap:      8385532      23964    8361568
```

Hm, Chromium and Firefox are supported in Ubuntu not Chrome.

In address bar type  **about:plugins** to see which version you have.

Check > free while you are playing flash
or start Chrome from terminal
> chrome

---

### Post by bman on 2013-01-02
Chrome has 11.5.31.5 of Flash installed.

How is Chromium supported and not Chrome, when I went and checked the Software Centre, Chromium was at a much lower version then Chrome is now? Which was weird to me, since Chromium is suppose to be newer.

```
             total       used       free     shared    buffers     cached
Mem:       8177352    4446232    3731120          0     115904    1055012
-/+ buffers/cache:    3275316    4902036
Swap:      8385532      10788    8374744
```

---

### Post by bman on 2013-01-03
Bump,

Still happening. Is there a newer Chromium version available outside the Software Centre?

---

### Post by evilsoup on 2013-01-03
Even if you want to use Chrome, testing to see if you get the same problem in Firefox will help determine if the problem is with Chrome, or with Flash.

---

### Post by addegsson on 2013-01-03
> **bman said:**
> Bump,

Still happening. Is there a newer Chromium version available outside the Software Centre?

Run these commands in Terminal:

sudo add-apt-repository ppa:a-v-shkop/chromium 
sudo apt-get update 
sudo apt-get install chromium-browser

---

### Post by bman on 2013-01-05
Can I run Chromium beside Chrome?

---

### Post by xc3RnbFO8P on 2013-01-05
Yes you can.

---

### Post by bman on 2013-01-05
So I couldn't test the videos because I would need to install the flash plugin, but it did fix other problems I have been having, so I'd say the problem is with Chrome.

Sucks, but thanks.

---

