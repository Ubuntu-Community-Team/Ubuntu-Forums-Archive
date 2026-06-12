---
title: "Firefox videos play with very slow audio"
date: 2019-07-30
forum: Multimedia Software
---

### Post by SeijiSensei on 2019-07-30
Most web videos play fine for me in Firefox. Occasionally on Twitter I'll come across a video that plays with the audio track at very slow speeds like this one: [https://twitter.com/ForTheRuleOfLaw/status/1155849832424202241](https://twitter.com/ForTheRuleOfLaw/status/1155849832424202241)

I've gone through the obvious [suggestions]("https://support.mozilla.org/en-US/kb/fix-common-audio-and-video-issues") at Firefox Support.  I've cleared the cache and disabled uBlock Origin and Ghostery all to no avail. A Google search doesn't bring up other postings about this issue.

I installed google-chrome-stable from the Google repository; it does not have this problem. Neither does chromium.

I'm using Firefox 68.0.1 on Kubuntu 19.04.

---

### Post by Autodave on 2019-07-30
68.0.1 with uBlock running: plays just fine here on Xubuntu 18.04.  I assume that you already tried an older kernel?

---

### Post by SeijiSensei on 2019-07-30
No, I haven't. Maybe that's the problem. It's strange that it's limited to certain videos though.

Update: Dropped back from 5.0.0-21 to 5.0.0-20. No change. Now I get the broken-video graphic from Twitter, though I got that occasionally on the newer kernel as well.

---

### Post by andrew.46 on 2019-07-30
> **SeijiSensei said:**
> Most web videos play fine for me in Firefox. Occasionally on Twitter I'll come across a video that plays with the audio track at very slow speeds like this one: [https://twitter.com/ForTheRuleOfLaw/status/1155849832424202241](https://twitter.com/ForTheRuleOfLaw/status/1155849832424202241)

Plays fine here with the latest Firefox Quantum 68.0.1. I believe that Firefox will use system FFmpeg for playback with some media files and this my be the issue on your system. FWIW I have a system install of the latest git FFmpeg here but I suspect a fully kitted-out version 4 and above would be equally as capable in this regard...

---

### Post by SeijiSensei on 2019-08-24
Problem persisted on three separate installations of Firefox with Kubuntu 19.04.  Switched to [Brave Browser]("https://brave.com/browser-option-a-hpa811/") which works fine.

---

