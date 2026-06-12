---
title: "Adobe Flash 64bit &quot;small fullscreen&quot; issue"
date: 2011-12-21
forum: Multimedia Software
---

### Post by dn* on 2011-12-21
Hi all

**_Background_**:

As per this post/comment:

[http://www.omgubuntu.co.uk/2011/10/flash-ubuntu-64-install-easily-1110/#comment-334232240](http://www.omgubuntu.co.uk/2011/10/flash-ubuntu-64-install-easily-1110/#comment-334232240)

I installed the official Ubuntu release of the 64bit version of Flash that Adobe released in the last few months.

Exact file/version: [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.1.102.55-0oneiric1_amd64.deb](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.1.102.55-0oneiric1_amd64.deb)

**_Problem_**:

When I go fullscreen on e.g. YouTube, most of the time it will not stretch to the full size of the screen, and is often a smaller video window than when it's embedded on the YouTube page. 

Screenshots show how it looks normally and then what happens when I go fullscreen.

Had it across different installations.:confused:

---

### Post by dn* on 2011-12-30
Are bumps allowed?

ATI 4770 card with default, non-proprietary drivers. Dual screen.

---

### Post by Paddy Landau on 2011-12-31
> **dn* said:**
> Are bumps allowed?
Yes, after 24 hours.

---

### Post by standev9 on 2012-06-19
I have the same problem too. Wasn't able to find any solution yet. Adobe Flash player version 11.0.1.152, 64bit distro.

---

### Post by Paddy Landau on 2012-06-19
Install the [Flash Aid plug-in for Firefox]("https://addons.mozilla.org/firefox/addon/flash-aid/"). Select Tools > Flash Aid > Wizard Mode. Follow the instructions. You may have to restart Firefox.

---

### Post by webgoddess on 2012-06-20
i'm having this issue too...i tried the **flashaid plugin** but it didn't fix the problem.  what's weird is that it was working just fine a couple days ago and the only thing i've done recently that i can think of was to install the **VLC plugin** for firefox.

i'm running **xubuntu precise x64**

---

### Post by webgoddess on 2012-06-20
i found a workaround, i installed the flashvideoreplacer and selected the "prefer webM when available" option and now youtube videos are working with HTML5 instead of flash ... this doesn't solve the original issue but it fixes the problem i've been having, i also can use that plugin to automatically launch VLC if i want to watch longer videos

---

### Post by Paddy Landau on 2012-06-20
> **webgoddess said:**
> i installed the flashvideoreplacer ...
I have not heard of FlashVideoReplacer before. It looks good and worth remembering.

---

### Post by standev9 on 2012-06-20
> **Paddy Landau said:**
> Install the [Flash Aid plug-in for Firefox]("https://addons.mozilla.org/firefox/addon/flash-aid/"). Select Tools > Flash Aid > Wizard Mode. Follow the instructions. You may have to restart Firefox.

Thank you very much! I've updated the Flash Player to the most recent version from Adobe and now fullscreen is working properly.

---

