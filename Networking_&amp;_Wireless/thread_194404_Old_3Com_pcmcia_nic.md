---
title: "Old 3Com pcmcia nic"
date: 2006-06-11
forum: Networking &amp; Wireless
---

### Post by snakedog on 2006-06-11
How do I get an old 3Com Etherlink III pcmcia card to run on a Compaq 12XL500 laptop running Xubuntu 6.06?  I've got a pcmcia Linksys EtherFast that Xubuntu picked up and config'ed right away, but we're a no-go on the 3C589D card.

Any suggestions?  Thanks...

---

### Post by xenon2000 on 2006-07-28
I don't have a solution, but I have the same setup, different laptop, and wanted to post my findings.

I have the 3C589D Etherlink III PCMCIA card as well. And also use Xubuntu 6.06 (laptop is an old IBM Thinkpad 390X P3-500mhz for low energy web server.)

I used the Xubuntu Alternate install CD and did the text install. Had the card plugged in the whole time. It works perfectly and fine after the install. But when I updated to linux-image-686 and upgraded, now the card does not work. It shows the card still and even gets DNS and gateway, but does not get an IP address. And even if I set it as static, it still does not ping.

But if I use an old 3com 10/100 CardBus card, it works fine with the updates and upgraded image. I have a feeling that the new PCMCIA tools broke things for me.

If anyone figures out how to get the 3c589D PCMCIA card to work with the latest updates to Xubuntu 6.06, let us know. For now I have to use the CardBus 3com nic.

---

