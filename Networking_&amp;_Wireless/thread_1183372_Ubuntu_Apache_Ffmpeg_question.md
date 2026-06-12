---
title: "Ubuntu Apache Ffmpeg question"
date: 2009-06-10
forum: Networking &amp; Wireless
---

### Post by rudjer on 2009-06-10
Hi friends!

I have just started using Apache server on Ubuntu, and have one question regarding a thing I want to do.

I want to use Apache as proxy to redirect web pages to server filter, which would take content of a page and transcode it so that mobile users can see web page on small display.
For the purpose of transcoding video clips and images, I decided to use FFMPEG. I installed ffmpeg and all required codecs.
But, when I go through proxy from some other computer, it just passes the traffic through, without invoking a filter. For example, when I go to Youtube and play some clip, it just goes through proxy, without executing the line with call to FFMPEG.

I'm attaching my httpd.conf file (The IP address of the server is masked, I have a proper one in the original file).

Please give me some suggestions on what could be wrong.

Also, if you have any good suggestion on what software I could use to transcode whole HTML pages to lower size, please tell me.

Thank you in advance!

---

