---
title: "Text Message Size"
date: 2022-02-18
forum: Mobile Technology Discussions (CLOSED)
---

### Post by angel mike on 2022-02-18
Is there a maximum size of Text Message that can be sent on a mobile ? In my case an Android Galaxy S9 using Pulse as the messenger. from doing a google it seems the limit might be 160 characters. If this is so I get no indication that a long text is sent until a shorter message is sent out asking if it had been received. The solution presumably is to send several shorter ones.
Some providers will automatically do do this but presumably not giffgaff !

---

### Post by coffeecat on 2022-02-18
Not an Ubuntu support question.

*Thread moved to **Mobile Technology Discussions**.*

---

### Post by schragge on 2022-02-18
> **angel mike said:**
> from doing a google it seems the limit might be 160 characters.
It is a bit more complicated than this, but yes, for an English text the limit is usually 160 characters. See [Message size]("https://en.wikipedia.org/wiki/SMS#Message_size") in the Wikipedia article. There's a little overhead when you're spreading a large message over multiple SMS.

---

### Post by #&amp;thj^% on 2022-02-18
> **schragge said:**
> It is a bit more complicated than this, but yes, for an English text the limit is usually 160 characters. See [Message size]("http://&quot;https://en.wikipedia.org/wiki/SMS#Message_size") in the Wikipedia article. There's a little overhead when you're spreading a large message over multiple SMS.

[s]This what I see from your link[/s] Link fixed
Sometimes just to avoid headaches I send multiple messages to avoid the 160 limit.

---

### Post by schragge on 2022-02-18
> **1fallen said:**
> This what I see from your link
Thanks. Fixed.

---

### Post by angel mike on 2022-02-19
Thanks all for confirming my assumption

---

### Post by angel mike on 2022-02-21
For anyone's interest I have changed from Pulse Messenger to Textra which gives you a warning on approaching the limit for a single text.

---

### Post by TheFu on 2022-02-21
SMS payload is 140 bytes. It uses the GSM control channel area. There's a header which contains necessary information to connect a call, just without the actual connection happening. Normal ASCII for printing for English is 7-bits and a byte is 8-bits, so that's where the slight difference between 140 and 160 comes.

Some SMS programs will automatically split longer messages into multiple texts.

SMS is not encrypted in any way. If you have a GSM radio, you can capture all the SMS messages from everyone.  GSM encryption is pretty weenie too, easily cracked, though it is illegal to do that. I think every newer version of GSM has slightly improved the encryption used, but govts don't really want it to be too strong.

If you care about security, don't use SMS.  There are alternative protocols available, some with some encryption and others with really good encryption. If you can, get your contacts to switch to a protocol with strong encryption. Most people don't really need to worry too much about it, but for the groups of people who may be harmed if their messages are seen by the wrong organizations or spies, the more that the rest of us encrypt and send, the more likely their truly life-critical messages will slip through.  Sorta like hiding a 4-leafed clover among all the clover on a hill.

---

### Post by coffeecat on 2022-04-29
This thread has become a magnet for idiotic spammers for some reason. (Sorry for the tautology!) Closed to prevent more unwanted garbage, at least in this thread.

---

