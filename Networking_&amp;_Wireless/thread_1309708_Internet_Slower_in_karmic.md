---
title: "Internet Slower in karmic?"
date: 2009-11-01
forum: Networking &amp; Wireless
---

### Post by karimruan on 2009-11-01
Has anybody else noticed this? Websites load considerably slower since my upgrade. And I mean way slower? Is this a problem with the compatibility between karmic and my wireless card?

---

### Post by Patman21 on 2009-11-01
I have had the same problem. It looks like karmic is using IPv6 for some reason. To fix firefox:
1. Type about:config into the address bar
2.  click 'I'll be careful, I promise!'
3. Paste this into the search field at the top of the page: network.dns.disableIPv6
4. Double click on the result so that it shows as 'true'
5. Restart the browser
6. ???
7. PROFIT!!!

---

### Post by karimruan on 2009-11-02
Nice, thanks a lot! I never thought Karmic would use IPv6, isn't that still a little new?

---

### Post by Foxcow on 2009-11-02
I was wondering if it was just my imagination.  Thank you!

---

### Post by karimruan on 2009-11-02
I wondered the same thing, until my wife complained about the speed issue. Then, I assumed my ISP cut back my bandwidth. I ran a test, was running at the speed I should be, just not when browsing the web. So I came here. THANKS AGAIN!

---

