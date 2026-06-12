---
title: "Will my old PC show streaming web video?"
date: 2012-09-11
forum: Multimedia Software
---

### Post by resander on 2012-09-11
The PC is an Athlon 1.6GHz with 512MB RAM and 40GB hard disk. 

On my main desktop (2.4GHz P4, 2GB ram) running Ubuntu 10.04 LTS streaming video works with Firefox. For example, the 'ticker-type' display at the top of the first page of the Daily Inquirer ([www.inquirer.net](www.inquirer.net)) shows all 10 items, videos and images (about half-half), but Ubuntu 10.04 LTS, Ubuntu 12.04 LTS, Xubuntu 12.04 and Lubuntu 12.04 (Quad-boot) on the Athlon only showed the images. The video window containing a triangular 'Start' button never appeared for Firefox, Chromium, Opera and Arora browsers for the video items. 

Other observations for the Athlon:

The Chromium browser reports 'shockwave flash plugin crashed' for all distros.

Arora only worked in text-mode for Lubuntu and crashed after a few minutes from Xubuntu 12.04.

Firefox on Ubuntu 10.04 complains about missing plugin, but did not tell which one, when playing many youtube videos.

Firefox on 10.04 could play some youtube videos, but these did not render on the other distros with Firefox. 

Movie players work when playing avi video files on Ubuntu 10.04/12.04 and Xububtu 12.04.

I am beginning to think 512MB is not enough for (streaming) videos from inside the browser.   

Q1. can I request log info from the browsers to help to pinpoint this problem, or can I get Firefox to tell me which plugin is missing?

Q2. anyone got streaming videos to work with 512MB memory with an Ubuntu?

Q3. anything else to try?

Ken

P.S.  I installed the 'restricted-extras' for all distros.

---

### Post by mikewhatever on 2012-09-11
512MB is not much, but it is more then enough to play streaming videos. In terms of resources, I'd say the CPU and graphics card would be the bottle necks, and an old PC will likely struggle, even with low quality videos.

Most streaming videos these days are Adobe Flash based, so to play them, you'll need to install the Adobe Flash plugin. Search for adobe-flashplugin in the Software Center and install it.

---

### Post by resander on 2012-09-11
Thanks Mike,

The adobe-flash plugin is already installed on Ubuntu 10.04 LTS, Ubuntu 12.04 LTS and Xubuntu 12.04. Probably by the restricted-extras that I installed for the quad-boot two days ago starting from scratch.

The explanation in Ubuntu Software Centre says the adobe-flash plugin installs the Adobe flash player that will work with Firefox, Chromium and a few more. It also says that installing the plugin will cause download of the adobe flash player from the Canonical partner archive. The three distros report that adobe-flash plugin has been installed, so I assume this step has worked.

Video is not totally absent. Some youtube videos work with Firefox on Ubuntu 10.04, for example Oscar Peterson's C jam blues (black and white 1964) but not Oscar Peterson's Hymn to Freedon in colour recorded 2008. However, C jam blues does not work at all with the other distros.

---

