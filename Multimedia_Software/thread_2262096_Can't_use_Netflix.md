---
title: "Can't use Netflix"
date: 2015-01-22
forum: Multimedia Software
---

### Post by hmunster123 on 2015-01-22
I'm trying to watch Netflix on Ubuntu but no luck. I installed Chrome Beta and the new agent string/spoofer. There is no choice for HTML5 in my Nefflix playback settings. Any suggestions? I just keep getting the error code **[COLOR=#B9090B]M7063-1913[/COLOR]**

---

### Post by sammiev on 2015-01-22
I just use the stable Google Chrome only. Type in Netfix.com and watch TV.

---

### Post by vinnywright on 2015-01-22
maby because it's beta ,,,,,,, chrome will play netflix ,,,,at least @hear  chrome version 40.0.2214.91 (64-bit)

[IMG]https://lh6.googleusercontent.com/-h55ddmExgZ4/VMHHkglmoBI/AAAAAAAABTw/I1YhLkW9gfE/s1152/snapshot10.png[/IMG]

---

### Post by monkeybrain20122 on 2015-01-22
Chrome stable would work. You don't need the beta.

---

### Post by kerry_s on 2015-01-23
> **hmunster123 said:**
> I'm trying to watch Netflix on Ubuntu but no luck. I installed Chrome Beta and the new agent string/spoofer. There is no choice for HTML5 in my Nefflix playback settings. Any suggestions? I just keep getting the error code **[COLOR=#B9090B]M7063-1913[/COLOR]**

just use regular chrome, no spoofing needed.

---

### Post by hmunster123 on 2015-01-23
Tried regular chrome, still get the error message.

---

### Post by ericbradshaw on 2015-01-23
Never got the error myself, but apparently you aren't alone. [Thread: [SOLVED] Netflix error code: M7063-1913 - and how I got it running natively in Chrome]("https://forums.opensuse.org/showthread.php/501137-SOLVED-Netflix-error-code-M7063-1913-and-how-I-got-it-running-natively-in-Chrome")

---

### Post by yancek on 2015-01-24
You should be able to install the update libnss3 software, which should be 3.16.2 or highter, from either the command line or the Software Center and that should resolve the problem.  If not, post back.

---

### Post by kostkon on 2015-01-24
You don't need to spoof your user agent string neither update your libnss3 anymore. It should work otb on chrome stable, unstable and beta.

---

### Post by hmunster123 on 2015-01-24
It also doesn't give me a choice to use HTML5, there's nothing there.

---

### Post by yancek on 2015-01-24
Are you using the current Ubuntu 14.04?  Did you download google-chrome from the repositories (don't think that would make any difference) and have you checked to see the version of libnss3 you have installed?

---

### Post by hmunster123 on 2015-01-24
Everything is current, I also don't understand why it doesn't give me a choice in player settings to choose which player I want to used, no HTML5 or Silverlight.

---

### Post by monkeybrain20122 on 2015-01-25
Chrome doesn't use silverlight.

---

### Post by yancek on 2015-01-25
If you have the current version of Ubuntu and the most recent release of google-chrome and libnss3.16 or newer, there is no reason it should not just work.  Some other problem then and there isn't an option for html5 because that is what is used.

---

### Post by yancek on 2015-01-25
If you have the current version of Ubuntu and the most recent release of google-chrome and libnss3.16 or newer, there is no reason it should not just work.  Some other problem then and there isn't an option for html5 because that is what is used.

When I installed an earlier version of google-chrome last summer, the option was there but I don't see it on the new version.

---

### Post by efflandt on 2015-01-27
When people were mentioning chrome I was wondering if they were refering to the chromium browser in the respositories (is google chrome actually there?). I also wonder whether the chromium browser in the Ubuntu repos works for Netflix.

I went right to google and installed Chrome from there and it works great for Netflix, I watched Death Race Inferno. It is better resolution than the old Netflix Desktop with MS Silverlight under wine that I used in 12.04 up until I recently installed 14.04.1. A long time ago I set that I prefer HTML5 somewhere on the Netflix website under my profile or preferences. Although, at the time Netflix still refused to do that for Linux Firefox and said it was not supported.

PS: I did get an error when I tried to play a Netflix video in current google chrome installed on USB 64-bit 14.04.1 live/install iso with persistence. But maybe something else on that is not up to date as a regular system that has been kept up to date or something to do with hybrid Intel/Nvidia graphics with default video drivers (using Intel graphics at the time).

---

