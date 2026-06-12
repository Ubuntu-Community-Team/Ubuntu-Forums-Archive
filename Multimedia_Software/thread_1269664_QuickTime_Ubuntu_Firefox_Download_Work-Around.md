---
title: "QuickTime Ubuntu Firefox Download Work-Around"
date: 2009-09-18
forum: Multimedia Software
---

### Post by wdelv on 2009-09-18
While the recent restrictions for playing QuickTime .mov files have been documented and discussed, I wanted to take a different approach.
I wrote a simple shell script which performs a wget on the URL targeting a specific .mov file from Apple's site and then executes totem on the file just downloaded.
That custom script works just fine.
What I'd like to do is automate the process in Firefox.
How do I automatically invoke my script?
How can I pass an argument to the script representing the target URL from a link in Firefox?

---

### Post by lovinglinux on 2009-09-18
> **wdelv said:**
> How do I automatically invoke my script?

If you are clicking the mov file directly, then you can specify which application to use with such type of file. Go to Firefox Preferences, then applications tab, then change the value for mov files, pointing to your script.

> **wdelv said:**
> How can I pass an argument to the script representing the target URL from a link in Firefox?

You can pass an argument by placing it after your command like this:

```
yourscript http://www.apple.com/whatever.mov
```

Then in your script, put **${1}** where the address of the video file should be. The number 1 represents the first argument passed with the previous command.

Nevertheless, it would be simpler if you install Greasemonkey extension for Firefox and use a script that allows to download videos from Apple. There are plenty of them.

---

### Post by wdelv on 2009-09-18
Thank you, lovinglinux, for your reply.
Regarding passing the URL as an argument, what I meant to ask is how I could easily invoke the command with the argument. Sure I could right-click on the link for properties, copy the URL in the clipboard, type a command in a terminal window, and paste the URL as an argument.
What I wanted to do is invoke the command with the argument in Firefox, if that is possible.
Maybe this kind of question should be posted in a Firefox-oriented forum if not here.

---

### Post by wdelv on 2009-09-19
Thanks, again, Lovinglinux, for the Greasemonkey tip.
This looks like the technology that will solve my problem.
While I have very limited Javascripting experience, this looks like something that I can get up to speed with in a short time.

---

### Post by lovinglinux on 2009-09-19
> **wdelv said:**
> Thanks, again, Lovinglinux, for the Greasemonkey tip.
This looks like the technology that will solve my problem.
While I have very limited Javascripting experience, this looks like something that I can get up to speed with in a short time.

You are welcome. There is no need to write the script yourself, because there are plenty of them at [http://userscripts.org](http://userscripts.org)

---

