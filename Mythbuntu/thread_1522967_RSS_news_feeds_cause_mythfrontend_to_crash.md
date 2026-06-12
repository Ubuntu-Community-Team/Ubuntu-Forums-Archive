---
title: "RSS news feeds cause mythfrontend to crash"
date: 2010-07-02
forum: Mythbuntu
---

### Post by Im In Deep on 2010-07-02
I am new to mythtv and downloaded the latest of mythbuntu (10.04) recently and have not been able to get the news feeds to work correctly. Whenever I open up an article it shows the downloading screen and some of the text starts to come up and then mythfrontend crashes. This happens no matter what news feed I subscribe to, the page starts to load and crashes.

It is strange that I can open up firefox and go to cnn.com just fine, but when I try to go to to a cnn.com page in news feeds the mythfrontend crashes. I am stuck and haven't been able to get past this. Any help is greatly appreciated!

Here is the very end of the log output from /var/log/mythtv/mythfrontend.log
I dont understand the HTTP 404 error since the website almost fully loads (text and pics) and then it crashes.

```

2010-07-02 20:49:19.730 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//info_menu.xml
2010-07-02 20:49:21.339 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter/news-ui.xml
2010-07-02 20:49:21.339 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/default/news-ui.xml
2010-07-02 20:49:21.941 NewsSite, Error: HTTP Protocol Error
            Explanation: 404: Not Found
2010-07-02 20:49:23.207 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter/browser-ui.xml
2010-07-02 20:49:23.208 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/default/browser-ui.xml
2010-07-02 20:49:23.219 MythUIWebBrowser: Loading css from - file:///usr/share/mythtv/themes/default/htmls/mythbrowser.css

(process:3997): GLib-GObject-CRITICAL **: /build/buildd/glib2.0-2.24.0/gobject/gtype.c:2706: You forgot to call g_type_init()

(process:3997): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(process:3997): GLib-GObject-CRITICAL **: g_object_new: assertion `G_TYPE_IS_OBJECT (object_type)' failed


```

---

### Post by elvinatom on 2010-07-04
It might be of little help to mention that I experience a similar behavior when attempting to play anything in "Internet Video", but maybe it's related

---

### Post by smarttowers on 2010-09-16
I am having the same problem with my mythbuntu install. I get it on the news feed load, trying to load a web page in the front end also. Don't know if this is solved but seems like a pretty big error. 

This is a frontend and backend install running on the same machine.

Seems unlikely this is a hardware issue but I am including my system specs in case there is some common issue to other posters.

My system is:
E2180 overclocked to 2.8ghz
2 gigs of crucial Ballistix DDR2 800
Gigabyte GA-73VM-S2 motherboard
MSI R4350-MD512 Radeon HD4350 video card
Older 120 gig IDE hard drive
Older 8x IDE dvd burner

I hope someone can help with this issue.

---

