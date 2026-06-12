---
title: "Download directly to SSH server via SOCKS?"
date: 2011-02-17
forum: Networking &amp; Wireless
---

### Post by poo706 on 2011-02-17
Here's the setup:

- SSH server on Maverick
- Connecting from Windows XP via putty
- XP Firefox using SOCKS proxy over SSH tunnel

What I would like to do is use XP Firefox to download large files from various file-hosters (Rapidshare, Hotfile...), but download them straight to Maverick instead of forwarding the download to XP.  Right now, my only option is to remote desktop into Maverick and download it using Ubuntu's Firefox.  And simply using wget did not prove to be simple.

Am I asking for the impossible?

[poo]

---

### Post by dmizer on 2011-02-17
You could ssh into Maverick with the -X or -C switch and open Maverick's firefox directly. Then when you saved it would save to Maverick.

You'd need an X server on your XP box. I used this: [http://x.cygwin.com/](http://x.cygwin.com/)

Once you get the X server working, you can ssh into Maveric like so:
```
ssh -C user@maverickip
```
Then you'll get a command line prompt. Just type:
```
firefox
```
And Maverick's firefox will open in XP. Anything you save will be saved on the Maverick box.

---

### Post by poo706 on 2011-02-17
Interesting idea, but I don't think that would satisfy my ultimate goal.  I'm in the very early stages of building Linux From Scratch.  In the end, I want to build an uber-lightweight, text-only OS.  I don't plan on even installing Firefox.  I was really hoping that it would simply be a matter of using XP Firefox to trigger the download, and then entering something like server:port:/path/to/downloads or whatever for the download location.

[poo]

---

### Post by poo706 on 2011-02-17
Looks like plowshare is what I've been looking for.  Just tried it out on Megaupload and Rapidshare and it worked beautifully!  Too bad there's no support for Hotfile, Fileserve, Filesonic, and Megashares, though.  Beggars can't be choosers.

[poo]

---

