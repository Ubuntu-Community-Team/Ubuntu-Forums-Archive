---
title: "How to configure apache:  SSL browsing, HTTP streaming?"
date: 2011-10-08
forum: Mythbuntu
---

### Post by johnlatz on 2011-10-08
I realize I'm probably trying to be too smart for my own good here, but still I thought I'd give this a try:

I'm running Mythbuntu 11.04 just fine, everything is tuned the way I wanted it except for one thing - I thought I'd play with turning on SSL for mythweb recently.  Since I have other pages being served on Apache that I did NOT want to impose SSL browsing on, I enabled SSL for mythweb by adding a link to "default-ssl" in /etc/apache2/sites-enabled, removed the link to mythweb.conf in the same directory, then added the line "Include sites-available/mythweb.conf" just before </VirtualHost> at the end of "default-ssl".

Pretty slick - all the configuration settings for mythweb are now underneath the :443 virtual host, mythweb is only served via HTTPS, and the rest of my webpages are unaffected.  Exactly what I was hoping for.

Except...  Streaming.  Now I can no longer stream - I like to stream my music collection to myself over the internet when I'm out of the house.

Yes, I know that most clients cannot receive streams over HTTPS.  Yes, I know that there is a radio box under "Mythweb -> Settings -> Streaming" that is titled "Force HTTP for streams".  That's currently checked, but still when I attempt to stream music, the *.m3u file is encoded[COLOR=#000000]  "https://<sitename>/mythweb/music/stream?i=3745".  Pasting that line into my media client "Open network stream" results in an error, pasting the same line but changing "https" to "http" results in a "cannot download" error.

So, my question is, how would I go about configuring Apache such that mythweb itself remains protected by SSL for browsing only, the rest of my directories are served by HTTP, and streamed media is served over port 80?
[/COLOR]

---

### Post by johnlatz on 2011-10-09
Continued to dink with this issue this evening, and came to realize my problem was a malformed cert.

I followed the directions in [https://help.ubuntu.com/11.04/serverguide/C/certificates-and-security.html](https://help.ubuntu.com/11.04/serverguide/C/certificates-and-security.html) to recreate my cert/key pair & restarted Apache, hit the website using Firefox on my client machine & downloaded the cert by clicking the blue field in the URL bar, and installed the resulting file in VLC via 'sudo cat *pem >> /etc/ssl/certs/ca-certificates.crt'.  Worked.

Somewhere last week, Googling for help, I found a note how to similarly install a cert for Windows Media Player using MMC.  When I can get my hands on a Windows machine again next week, I'll see how that works.

---

