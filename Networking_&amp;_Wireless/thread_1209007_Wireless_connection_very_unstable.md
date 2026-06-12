---
title: "Wireless connection very unstable"
date: 2009-07-09
forum: Networking &amp; Wireless
---

### Post by dismas on 2009-07-09
I installed Ubuntu 9.04 and am very satisfied except network performance is very unstable (compared to when I was using Windows Vista previously). I am using an Airlink AWLL3028 wireless USB adapter. Setting up the WPA connection was successful. However performance is poor. The connection strength is around 50%, but actual Internet browsing is spotty. Browsing would be quick and responsive for a few minutes then really slow for the next few. I thought it might be just Firefox, but Opera, Midori, and even Lynx had the same problems. I tried ping 192.168.0.1 (my router) and it would miss packets or have delayed replies corresponding to when my browsing was slow. What could be the problem? Thanks for your time.

---

### Post by superprash2003 on 2009-07-10
you could try changing your DNS servers to opendns - 208.67.222.222 and 208.67.220.220

---

### Post by dismas on 2009-07-10
Thanks for the advice, however my problem still persists unfortunately. Is there a way to get "better drivers" in this case? Not that I know if the drivers are the problem.

---

### Post by RavanH on 2009-07-12
Very slow and unstable connection was what I ran into and solved by installing Wicd (replacing Network Manager) and using a small pre-connection script to force higher than 1Mb connection rate which seems RT2500 specific, so might not apply to your case. Try Wicd first and then maybe follow up on the last two steps on [http://ubuntuforums.org/showthread.php?p=7605785](http://ubuntuforums.org/showthread.php?p=7605785)

Hope it helps you out.

---

