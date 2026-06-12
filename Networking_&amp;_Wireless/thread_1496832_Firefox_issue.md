---
title: "Firefox issue?"
date: 2010-05-29
forum: Networking &amp; Wireless
---

### Post by Komputor on 2010-05-29
Thanks ahead of time to everyone that can help!
  I am having some hang issues with firefox and am not sure what can be the problem.  Here is my specs:
Toshiba Satellite L35 Laptop
Ubuntu 10.4 Lucid / Windows Vista Home Basic dual boot
Atheros Integrated NIC
Firefox v3.6.3

Everything is working fine on the network side, being confirmed by both my wife's EEE Netbook, and my iPod(r) Touch.  There is no problem with my network interfaces, or my interface card, as confirmed by the other devices' ability to connect and browse at normal speeds.

However; with my lappy running Ubuntu and Firefox, a LOT of websites hang/lag when attempting to browse websites.  I have read on some of the forums about disabling ipv6 through the "about:config" option and that seemed to help a little, but not to where it should be.  I have tried a lot of options, but it is still lagging.

If anyone has any good input, again, thanks in advance!

---

### Post by wojox on 2010-05-29
Have you tried this thread [Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567")

---

### Post by utnubuuser on 2010-05-29
You can disable ipv6 in GRUB2 as well, and that actually seems (I stress the word **seems**) to make more of a difference.

In /etc/default/grub look for the line that reads:> GRUB_CMDLINE_LINUX=""and inside the paranthesis add:"ipv6.disable=1"
save, then in a terminal, do: > sudo update-grub and reboot - might help, might not.  Seemed to make a difference in my system.
I had a bit of an issue with firefox at first, removed the search-bar from the panel and things improved.

---

### Post by Komputor on 2010-05-29
@utnubuuser:
  Tried your script edit and here's what happened:
1. Edited grub file with gedit normally
2. Upon reboot, Ubuntu would NOT load.
3. Had to start in root session, vi-edit the grub file and remove the changes made by your suggestion.

Everything came back normally and nothing bad changed that I can tell so far.  The grub file is the same as it was before I changed it.

---

### Post by wojox on 2010-05-29
Try this [http://wojox.homelinux.org/?p=46](http://wojox.homelinux.org/?p=46)

---

### Post by Komputor on 2010-05-29
@wojox:
  Sorry for trying the easiest route first, but can you blame me?  I have viewed your link and it seems there is a lot of things that need to be looked at and measured before any real progress is made.  I will look at it again, with a more open mind, but I was wondering if there is a network setting I can change that would optimize my browsing speed, not a browser tweak that may or may not harm the overall performance of my lappy.

---

### Post by wojox on 2010-05-29
The only network setting I know of is disabling ipv6. Other than that it's browser tweaks from lovinglinux's howto.

---

### Post by Komputor on 2010-05-29
Trying now

OK, so the last code from wojox seemed to work at disabling ipv6.  But Firefox is still hanging trying to load the next page.  On to lovinglinux's site.

---

### Post by Komputor on 2010-05-30
> **wojox said:**
> Have you tried this thread [Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567")
 
Well, it seems there are a few differences between my firefox and the methods described here. I am resolving to repairing the program by removing and then re-installing the whole thing. I am not sure but there are some problems with the browser itself. I am using Epiphany right now and it is LIGHTNING faster than firefox. Not sure what is going on exactly, but I think a fresh re-install will *hopefully* help.
 
Udate:
Unable to correct the issue, and it is definately a Firefox hang up.  Not sure if Firefox is unable to talk to my wireless adapter, or if it's something in the setup.  Disabling ipv6 only seems to help very little.  Nothing I have tried so far is helping Firefox actually work :(  The browser hangs on every page, every link.  Also, every time I click on a .php link, Firefox asks me what application to open it with.  Not sure what's up with that, but this whole thing definately requires a bug report.
 
Also, Wojox's FIRST suggestion link (lovinglinux's page) is helpful for anyone having this, or other issues.  Definately a first stop!  I noticed a few differences between my output and the links' descriptions.
From the Preferences Tweaks link and comparing my output:
       <Setting>                              <Value>
network.dns.disableIPv6                    True
network.prefetch-next                       True
network.http.pipelining                      False
network.http.pipelining.maxrequests     4
network.http.proxypipelining              False
browser.cache.memory.capacity        >No such option/no value
browser.cache.check_doc_frequency    3
network.dns.CacheEntries                 >No such option/no value
network.dns.CacheExpiration             >No such option/no value
nglayout.initialpaint.delay                >No such option/no value
 
So if anyone has a suggestion, I would like to hear it.

---

### Post by Komputor on 2010-06-02
Ok, so I found these settings on you tube ([http://www.youtube.com/watch?v=vdmgrqckla0](http://www.youtube.com/watch?v=vdmgrqckla0)) and also reported the bug to Bugzilla, ([https://bugzilla.mozilla.org/show_bug.cgi?id=569473](https://bugzilla.mozilla.org/show_bug.cgi?id=569473)).  For a quick reference to the settings in about:config that are altered:
Code:
about:config 
 
accessibility.blockautorefresh = true 
browser.blink_allowed = false 
browser.cache.disk_cache_ssl = true 
browser.cache.memory.enable = true 
browser.cache.offline.capacity = 1024000 
browser.chrome.site_icons = false 
browser.chrome.toolbar_tips = false 
browser.download.manager.closeWhenDone = true 
browser.download.manager.scanWhenDone = false 
browser.fullscreen.animateUp = 0 
browser.fullscreen.autohide = false 
browser.history_expire_days_min = 0 
browser.history_expire_sites = 0 
browser.search.openintab = true 
browser.sessionhistory.max_total_viewers = 1 
browser.tabs.closeButtons = 0 
browser.tabs.loadFolderAndReplace = false 
browser.tabs.tabClipWidth = 70 
browser.tabs.tabMinWidth = 70 
browser.urlbar.autoFill = false 
browser.urlbar.clickSelectsAll = false 
browser.urlbar.maxRichResults = 0 
config.trim_on_minimize = true (boolean) 
content.interrupt.parsing = true (boolean) 
content.max.tokenizing.time = 2250000 (integer) 
content.maxtextrun = 8191 (integer) 
content.notify.backoffcount = 5 (integer) 
content.notify.interval = 750000 (integer) 
content.notify.ontimer = true (boolean) 
content.switch.threshold = 750000 (integer) 
dom.max_script_run_time = 20 
extensions.getAddons.maxResults = 3 or 10 
javascript.options.jit.chrome = true 
javascript.options.jit.content = true 
keyword.enabled = false 
layout.spellcheckDefault = 2 
layout.word_select.eat_space_to_next_word = false 
layout.word_select.stop_at_punctuation = false 
network.dns.disableIPv6 = true 
network.dns.ipv4OnlyDomains = localhost 
network.http.max-connections = 100 
network.http.max-connections-per-server = 32 
network.http.max-persistent-connections-per-proxy = 16 
network.http.max-persistent-connections-per-server = 50 
network.http.pipelining = true 
network.http.pipelining.firstrequest = true (boolean) 
network.http.pipelining.maxrequests = 300 
network.http.pipelining.ssl = true 
network.http.proxy.pipelining = true 
network.http.proxy.version = 1.0 
network.http.redirection-limit = 32 
network.http.request.max-start-delay = 0 
network.prefetch-next = false 
nglayout.initialpaint.delay = 100 (integer) 
plugin.expose_full_path = true 
security.dialog_enable_delay = 0 
toolkit.scrollbox.scrollIncrement = 75 
ui.submenuDelay = 0 (integer) 
view_source.editor.external = true 
view_source.editor.path = (path of the editor) 
zoom.maxPercent = 400 

Some of these settings are not in my about:config, so I went ahead and skipped those that simply were not there.  All you have to do is enter the description before the '=' and set the value to the same as after the '='.

Although this did help DRAMATICALLY with my FF speed, it still does hang quite a bit, and nothing seems to help actually ELIMINATE the problem.  I am so very tired of refreshing pages over and over just to view it.  Let alone if I need to enter login info, the hang will drop the data and I am stuck in a continuous login loop!

I have a feeling the problem lies with FF and my NIC.  By the way, I have absolutely NO problems with downloading files or packages, ONLY browsing.  Any suggestions will be greatly appreciated.

---

### Post by Komputor on 2010-10-14
BUMP!
This thread definitely needs a bump since my issue is STILL not worked out and I am indeed getting very tired of it!!!! NOT a happy camper at all :(

---

### Post by ebasa on 2010-10-14
Firefox v3.6.3 is seriously out of date, it was also very unstable on my system. Firefox is now up to v3.6.10

---

### Post by Komputor on 2010-10-14
Ebasa:
I have already updated to the latest Firefox (v3.6.10).  I am still having these same problems.  Like I said in the previous posts, I can eventually get to the page I am requesting (usually), but it seems to be a problem with Firefox "talking" to my Network Interface Card.  I am still very able to update and download package updates, software, and other things that do not have anything to do with the Firefox browser.  I can't for the life of me figure this out!  I have heard nothing back from bugzilla and I am quite at the end of my rope here.  If anyone has any suggestions, I am open to them.  I am about to do a fresh install of Ubuntu to see if that will help.

---

### Post by mbott on 2010-10-15
My issue may be similar, but it is different.  :(

Firefox through 9.10 has been my browser of choice.  When I updated to 10.4.1 LTS, browsing with Firefox became a chore: pages taking 20 to 30 seconds to load.  Since 10.4.1 was just a stop to get to 10.10, I didn't worry about it.

Same issues with 10.10.  20 to 30 seconds minimum and longer to load a page, any page.  Dumped all Firefox addons, etc, but nothing has helped.  For grins, I loaded Chrome and the issues are non-existent...but **only** for Chrome.  Just wish I liked Chrome.  :(  [COLOR="Red"]Edited to add: even though Chrome worked, I just uninstalled it.[/COLOR]

I'll poke around in Firefox over the next couple of days and try to figure out why it's such a pig and Chrome isn't.

[COLOR="Red"]2nd Edit:  Issue resolved for me by changing the DNS Servers in the network manager to the Google Public DNS Servers.[/COLOR]

-- 
Mike

---

### Post by Komputor on 2010-10-16
Well I installed Google Chrome and the same problems are encountered. I am wondering if there might be a script I need to edit somewhere. I am going to contact Canonical about this as it is so very frustrating!

---

