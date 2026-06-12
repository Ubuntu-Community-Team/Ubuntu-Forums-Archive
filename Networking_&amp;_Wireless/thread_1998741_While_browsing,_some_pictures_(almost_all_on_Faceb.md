---
title: "While browsing, some pictures (almost all on Facebook) are not loaded/displayed"
date: 2012-06-07
forum: Networking &amp; Wireless
---

### Post by cpury on 2012-06-07
Hey everyone!
This is a really odd thing that I have no explanation for. I'm using Ubuntu 12.04 32-Bit. This issue is not connected to a certain browser, it looks the same on any. However, on the same computer I also have a Windows 7 installation, where I have no problems surfing.

Basically what happens is this:
[http://askubuntu.com/questions/125737/facebook-pictures-not-showing-up](http://askubuntu.com/questions/125737/facebook-pictures-not-showing-up)

Most of the pictures on Facebook will just not be loaded. Some are displayed, however. Very rarely it also happens to other websites (for months I couldn't read XKCD). Also it varies at certain times. Some days I can see 90% of the pictures, but mostly it's just around 20%.

When trying to open the URL of such an image, Opera says:
Could not connect to remote server
All of FB's profile pictures are on the server profile.ak.fbcdn.net. Also the ones that are displayed. But when I try to ping that server I get:
ping: unknown host profile.ak.fbcdn.net

I am totally confused by this behavior, but googling has found that some other people are struggling with the same issue (as on the link above), but no one found a solution so far. It's very annoying...

Thank you for any help you can provide!

---

### Post by arabuli on 2012-09-16
Hi cpury,

I'm the guy with the same problem from Askubuntu. And I just received solution for our problem. Thanks to Askubuntu user Mik. You should change your ISP's dns to Google's public dns. Change it to 8.8.8.8 and it should work fine. You can see the conversation [here]("http://askubuntu.com/questions/125737/facebook-pictures-not-showing-up")

---

### Post by cpury on 2012-09-16
Thanks a lot for the notification, arabuli! I have moved to another place and not had this issue since, so I can't confirm whether the solution would have worked for me, but I'm glad if it did so for you!

Cheers

---

### Post by tienlbhoc on 2012-09-16
sometimes firefox have this error, because of cache, I cleared cache (or remove and reinstall) or using chrome.

---

