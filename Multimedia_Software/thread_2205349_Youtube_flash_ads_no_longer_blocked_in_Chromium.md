---
title: "Youtube flash ads no longer blocked in Chromium"
date: 2014-02-13
forum: Multimedia Software
---

### Post by street spirit on 2014-02-13
I'm using Chromium 32.0.1700 on Kubuntu 13.10 with the Adblock Plus extension. Up until about a week ago, all ads on Youtube were reliably hidden, but for some reason that doesn't work anymore. All I've been able to find about this is that there is apparently a problem between Chrome 32 and one version of the Flash plugin (NPAPI or PPAPI), but that was on Windows. I'm not sure how to apply the suggested solution on Ubuntu, where I install the plugin with the package manager instead of manually.

Chromium shows this plugin on the chrome://plugins page:

```
   Adobe Flash Player - Version: 11.2 r202
          Shockwave Flash 11.2 r202
```

**aptitude show flashplugin** returns the following list:

```
    p   adobe-flashplugin                     - Adobe Flash Player plugin version 11
    p   adobe-flashplugin:i386                - Adobe Flash Player plugin version 11
    v   flashplugin-downloader                -
    c   flashplugin-downloader:i386           - Adobe Flash Player plugin installer (transitional package)
    i   flashplugin-installer                 - Adobe Flash Player plugin installer
    p   flashplugin-installer:i386            - Adobe Flash Player plugin installer
    v   flashplugin-nonfree                   -
    v   flashplugin-nonfree:i386              -
    p   flashplugin-nonfree-extrasound:i386   - Adobe Flash Player platform support library for Esound and OSS
```

Any idea what I should try to solve the problem?

---

### Post by howefield on 2014-02-13
Enable html5 : [http://www.youtube.com/html5](http://www.youtube.com/html5) and/or use pepperflash ?

---

### Post by monkeybrain20122 on 2014-02-13
> **street spirit said:**
> I'm using Chromium 32.0.1700 on Kubuntu 13.10 with the Adblock Plus extension. Up until about a week ago, all ads on Youtube were reliably hidden, but for some reason that doesn't work anymore. All I've been able to find about this is that there is apparently a problem between Chrome 32 and one version of the Flash plugin (NPAPI or PPAPI), but that was on Windows. I'm not sure how to apply the suggested solution on Ubuntu, where I install the plugin with the package manager instead of manually.



I think google pays the dev of adblock plus to unblock google ads. That leads to a pissed off user who forked it to adblock edge, but since he has something against google it won't work on Chromium or Chrome, it is Firefox only. Google adblock edge if you want to know about the back story (irony intended :))

---

### Post by tgalati4 on 2014-02-13
I thought Chrome used a version of flash called Pepper Flash which AdBlock couldn't control.  This allows ads obviously.  So did you update Chrome recently?  Like perhaps a week ago?

---

### Post by monkeybrain20122 on 2014-02-13
> **tgalati4 said:**
> I thought Chrome used a version of flash called Pepper Flash which AdBlock couldn't control.  This allows ads obviously.  So did you update Chrome recently?  Like perhaps a week ago?

OP is using chromium so there is no pepper flash.

---

### Post by howefield on 2014-02-13
> **monkeybrain20122 said:**
> OP is using chromium so there is no pepper flash.

No, but it can be installed.

Not the first thread I've seen on this, but working fine for me on both Chromium and Firefox.

---

### Post by street spirit on 2014-02-13
Thank you all for your help.

Pepperflash: Interesting. I have to admit I haven't heard of this before. Maybe it's only bundled with Chrome (as opposed to Chromium), because my Flash plugin identifies itself as "Adobe Flash Player", presumably installed with the flashplugin-installer package.

Adblock Edge: that's what I use on Firefox. AFAIK it's not just Google paying the author of the original Adblock Plus extension, but ABP generally selling out and letting advertisers white-list themselves, as well as receiving usage statistics. I'd love to use Adblock Edge on Chromium, but it's not available in the Chrome Web store.

HTML5 player on Youtube: that's a very good idea. I've heard mixed reports about how well it works and what percentage of videos is available for it, but a quick test was very encouraging. I think that's what I'm going to use until the plugin/browser incompatibility is resolved.

I'm going to use HTML5 mode for now and leave this thread as unsolved for a little while, in case somebody can suggest a solution for the Flash plugin, too.

---

### Post by monkeybrain20122 on 2014-02-13
> **howefield said:**
> No, but it can be installed.

Not the first thread I've seen on this, but working fine for me on both Chromium and Firefox.

Yeah you're right but I wouldn't assume that OP has gone out of his way to install pepper flash, besides the output in the first post shows flash 11.2 :)

---

### Post by monkeybrain20122 on 2014-02-13
> **street spirit said:**
> 
 I'd love to use Adblock Edge on Chromium, but it's not available in the Chrome Web store.
.

It won't be unless someone forks it, he said something to the effect that if you use the products by an adware company you should enjoy the ads. :)

---

### Post by howefield on 2014-02-13
> **monkeybrain20122 said:**
> Yeah you're right but I wouldn't assume that OP has gone out of his way to install pepper flash, besides the output in the first post shows flash 11.2 :)

I mentioned pepperflash as a potential solution, not that the OP already had it. :)

---

