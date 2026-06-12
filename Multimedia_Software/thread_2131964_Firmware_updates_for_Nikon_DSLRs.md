---
title: "Firmware updates for Nikon DSLRs"
date: 2013-04-03
forum: Multimedia Software
---

### Post by chili555 on 2013-04-03
If you own a recent Nikon DSLR, you may be aware that a number of firmware updates have been released. As of today, they include the D4, D600, and D800 as well as the D3, D3s, D3x, D7000, and D3200. I suspect that more may be added. 

Nikon's instructions are easy to follow and download links are given for Windows and Mac platforms. However, being a Linux nerd and a semi-absolutist, I experimented and found a way to accomplish everything in Ubuntu. No Windows computer is needed, which is a good thing, since I don't own any!

Here are Nikon's instructions: [http://support.nikonusa.com/app/answers/detail/a_id/18257/kw/D800](http://support.nikonusa.com/app/answers/detail/a_id/18257/kw/D800) This link is for the D800. While the instructions are similar, the firmware files are not. Be sure to find the page for your exact Nikon model.

I followed the instructions exactly but downloaded the Windows .exe to a folder I named D800Firmware. Then I opened a terminal and did:```
cd D800Firmware
unrar e F-D800*
```unrar graciously extracted the .bin file referred to in the instructions and I continued with the firmware update. It went perfectly. I was quite confident it would, having updated firmware on several other Nikon DSLRs previously with no problem at all.

I hope my experience may be helpful.

---

### Post by slickymaster on 2013-04-03
Thank you for the heads up, chili555. I have a DSLR D70, and thanks to you, I now know that it's firmware has been updated in 03/29/2013.

When I'll get home I'll try to proceed with the installation in my Ubuntu box. Tell me just one thing, did you use an approved CF card in the camera, like suggested at Nikon's website, or did you manage to do it with a Microdrive card?

---

### Post by chili555 on 2013-04-03
I use Sandisk Extreme CF cards. I have no idea if they are on Nikon's approved list, but I have used them in various sizes since my first DSLR. I have never had one fail or hiccup.

Please post back your experience so the searchers will see how smoothly it goes.

---

### Post by slickymaster on 2013-04-03
> **chili555 said:**
> ... I have no idea if they are on Nikon's approved list, ...

That's the reason I asked. I haven't manage to find such a list at Nikon's website.

Anyway, I'll try to do it with the card I have and see how it will work.

---

### Post by chili555 on 2013-04-03
> **slickymaster said:**
> I haven't manage to find such a list at Nikon's website.


[http://support.nikonusa.com/app/answers/detail/a_id/9601/~/approved-cf-cards---d70-%2F-d70s](http://support.nikonusa.com/app/answers/detail/a_id/9601/~/approved-cf-cards---d70-%2F-d70s)

Here ya go!

---

### Post by slickymaster on 2013-04-03
> **chili555 said:**
> [http://support.nikonusa.com/app/answers/detail/a_id/9601/~/approved-cf-cards---d70-%2F-d70s](http://support.nikonusa.com/app/answers/detail/a_id/9601/~/approved-cf-cards---d70-%2F-d70s)

Here ya go!

Thanks a lot.
It turns out I had a misspelled on my query terms. :mad:

---

### Post by chili555 on 2013-04-03
I'm pretty sure many of the cards mentioned are available at reasonable prices at a variety of nearby big box stores. CF card is the only method I've ever used and therefor the only method I recommend. Other methods may work just fine but I haven't tried them and can't vouch for them. Dr. Chili recommends you always flash firmware responsibly!

---

### Post by slickymaster on 2013-04-03
> **chili555 said:**
> ... CF card is the only method I've ever used and therefor the only method I recommend. ...

Completely agree with you. My issue is that I only have a few Kingston's 16 GB 266x CF cards and the list just mention SanDisk, Lexar and Renesas.
But I'll give it a try anyway.

---

### Post by slickymaster on 2013-04-04
> **chili555 said:**
> 
I followed the instructions exactly but downloaded the Windows .exe to a folder I named D800Firmware. Then I opened a terminal and did:```
cd D800Firmware
unrar e F-D800*
```unrar graciously extracted the .bin file referred to in the instructions and I continued with the firmware update. It went perfectly. I was quite confident it would, having updated firmware on several other Nikon DSLRs previously with no problem at all.

I hope my experience may be helpful.

Again, thank you.

Did it the way you suggest for my D70, and worked like a charm.

Edit: By the way, didn't get any problems with my CF cards.

---

