---
title: "Firefox for Linux media, videos, maps much slower and resource intensive than Chrome"
date: 2016-02-16
forum: Multimedia Software
---

### Post by bgc on 2016-02-16
Apologies for cross-posting (also on Mozilla support forum), but I'm not sure whether the issue here is Firefox or Ubuntu.

I am partial to running Firefox over Chrome, however, there are several instances when the difference between the two is abysmal.

Whenever I play any videos (for example Youtube), browse any maps (Nokia Here, Google Maps), or do anything that requires media (Skype, Google Hangouts), Firefox is slow, a single core will go to 100%, Firefox will become slow to respond, and sometimes will hang. On the other hand, these same sites on Google Chrome (or Chromium) will be perfectly smooth and fast.

I have searched for several solutions, including enabling/disabling hardware acceleration, checking that addons are not the culprit, checking that the plugins are up to date, and so on, to no avail. I have also followed Mozilla's "high CPU" and "high RAM" pages, but finding no solution.

The issue may be related to the following process

```
/usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 vt7 -novtswitch
```

For instance, if I zoom on a map, this process will go up to 100% of a CPU. Switching to GDM does not solve the problem - the same process shows up (albeit gdm). This process does not behave the same way when performing the same actions in Google Chrome/Chromium.

Does anyone have any suggestions?

```
System details:

HP EliteBook with onboard Intel graphics.
Ubuntu 14.04.
Firefox 44.0.2.
i3 window manager.

Installed Plug-ins
    DivX Web Player version 1.4.0.233
    The IcedTea-Web Plugin executes Java applets (IcedTea-Web 1.5.3 (1.5.3-0ubuntu0.14.04.1))
    The Videos 3.10.1 plugin handles video and audio streams.
    Shockwave Flash 11.2 r202
    Shockwave Flash 20.0 r0
    VLC video player 3.10.1 plugin
    Totem video player 3.10.1 plugin
    Google Talk Plugin Version: 5.41.0.0
    Google Talk Plugin Video Renderer Version: 5.41.0.0 

Application
    Firefox 44.0.2
    User Agent: Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:44.0) Gecko/20100101 Firefox/44.0
    Support URL: [https://support.mozilla.org/1/firefox/44.0.2/Linux/en-GB/](https://support.mozilla.org/1/firefox/44.0.2/Linux/en-GB/)

Extensions
    Download Manager (S3) 4.02 (s3download@statusbar)
    DownThemAll! 2.0.18.1-signed.1-let-fixed ({DDC359D1-844A-42a7-9AA1-88A850A938A8})
    Ghostery 5.4.10 (firefox@ghostery.com)
    Google Analytics Opt-out Browser Add-on 0.9.8 ({6d96bb5e-1175-4ebf-8ab5-5f56f1c79f65})
    HTTPS-Everywhere 5.1.2 (https-everywhere-eff@eff.org)
    LastPass 3.2.42 (support@lastpass.com)
    uBlock Origin 1.6.0 (uBlock0@raymondhill.net)
    Vimperator 3.11.3 (vimperator@mozdev.org)
    Ubuntu Modifications 3.2 (ubufox@ubuntu.com) (Inactive)

Javascript
    incrementalGCEnabled: True

Graphics
    adapterDescription: Intel Open Source Technology Center -- Mesa DRI Intel(R) HD Graphics 5500 (Broadwell GT2)
    adapterDeviceID: Mesa DRI Intel(R) HD Graphics 5500 (Broadwell GT2)
    adapterDrivers:
    adapterRAM:
    adapterVendorID: Intel Open Source Technology Center
    driverDate:
    driverVersion: 3.0 Mesa 10.3.2
    failures: [u'[GFX1-]: GLContext is disabled due to a previous crash.', u'[GFX1-]: GLContext is disabled due to a previous crash.', u'[GFX1-]: GLContext is disabled due to a previous crash.', u'[GFX1-]: GLContext is disabled due to a previous crash.', u'[GFX1-]: GLContext is disabled due to a previous crash.', u'[GFX1-]: GLContext is disabled due to a previous crash.']
    indices: [0, 1, 2, 3, 4, 5]
    info: {u'CairoUseXRender': 1, u'AzureCanvasBackend': u'cairo', u'AzureFallbackCanvasBackend': u'none', u'AzureContentBackend': u'cairo', u'AzureSkiaAccelerated': 0}
    numAcceleratedWindows: 0
    numAcceleratedWindowsMessage: [u'']
    numTotalWindows: 1
    supportsHardwareH264: No;
    webglRendererMessage: [u'']
    windowLayerManagerRemote: True
    windowLayerManagerType: Basic

Misc
    User JS: No
    Accessibility: No
```

---

### Post by shantiq on 2016-02-17
Hi there FF is the slowest of all the browsers for me and always has been; but then again it does things that others do not so therein lies the trade-off
night_sky2 on this forum  suggested the [following modifications]("http://ubuntuforums.org/showthread.php?t=2308244&p=13420020#post13420020") to speed up FF **generally**

;I made a note of those; and I must say it  moves mine quicker than before:

Personally I use other browsers [Palemoon/Midori/otter-browser]]for speed and day-to-day and FF for specific tasks only; anyway here goes:


speed up Firefox >>

[https://addons.mozilla.org/en-US/firefox/addon/classicthemerestorer/](https://addons.mozilla.org/en-US/firefox/addon/classicthemerestorer/)
also


THEN  >> about:config       then set

Firefox Hello (built-in app for voice chat and video call): **loop.enabled -> false**

Pocket (built-in app to manage reading lists and internet articles): **browser.pocket.enabled -> false**

Reader View (extracts web articles and display them like on Android): **reader.parse-onload.enabled -> false**

WebRTC (browser-to-browser app to allow voice chat and call): **media.peerconnection.enabled -> false**
[B]media.peerconnection.identity.enabled -> false
media.peerconnection.use_document_iceservers -> false
media.peerconnection.video.enabled -> false[/B]

PDF Reader (built-in reader in Firefox for PDF files): **pdfjs.disable -> true**

Tab audio indicator (display icon on a tab when sound is playing from the website): **browser.tabs.showAudioPlayingIcon -> false**

Geolocalization (allow some websites to request and pinpoint your geographic location): **geo.enabled -> false**



there are probably other settings which also increase speed but these are a start anyway

---

### Post by bgc on 2016-02-17
Thanks for the tips! I'll certainly use some of them.

After much playing around (graphics card drivers, WebGL, etc.), I think I have found the culprit: [FONT=Courier New]gfx.xrender.enabled[/FONT] needs to be set to false, and that makes a world of difference.

---

### Post by Tom_Temple on 2016-02-26
Where do I find   config       then set    ?

---

### Post by shantiq on 2016-02-27
enter

```
about:config
```   in url box    then you will see it all there

---

### Post by bgc on 2016-02-29
Then search for "xrender", and you should see the setting there. It is enabled by default. Set it to "false".

---

