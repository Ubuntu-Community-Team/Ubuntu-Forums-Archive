---
title: "DNS Errors causing posfix to fail at sending mail"
date: 2009-09-15
forum: Networking &amp; Wireless
---

### Post by kempy1000 on 2009-09-15
Hi

I have just installed a mail server to my ubuntu server.

I used the command sudo tasksel and selected mail server to install it all.

However it all worked untill i came to send an email! I tried to send an email to my gmail account and i got the error:
```

Host or domain name not found. Name service error for name=gmail.com type=MX: Host not found, try again

```

So after searching the forums (much in the archives) I found some help suggesting my DNS maybe at fault so I tried to run:
```

dig mx @195.175.39.39 gmail.com

```

The output:
```

; <<>> DiG 9.5.1-P2 <<>> mx @195.175.39.39 gmail.com
; (1 server found)
;; global options:  printcmd
;; connection timed out; no servers could be reached

```

Now the thread said I should have a much different output from this command.

So I presume the DNS on my server is somehow blocked or broken.

Any help is appreciated
Thanks
Chris

---

