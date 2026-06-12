---
title: "IP access on dual boot system."
date: 2012-03-30
forum: Networking &amp; Wireless
---

### Post by NRV on 2012-03-30
here's the scenario:

- one computer - dual boot, Windows and Ubuntu
- IP address # 1 is the IP address assigned by Windows and IP address # 2 is assigned by Ubuntu
- web-based access to IP addresses is through iPad browser
- on the iPad, using the browser, IP address #1 can be accessed but not IP address #2
- ping shows both IP addresses as receiving all transmitted packets (0% loss)

is it possible to access IP address #1 if the computer is logged in to Ubuntu? tia.

---

### Post by Ms. Daisy on 2012-03-30
Welcome to the forums.

Are you using a router to connect the computer to the internet? Or is it using the ipad's internet connection?

edit: forgot to ask - What are you trying to do with the IP?

---

### Post by BertN45 on 2012-03-30
The answer is no. If you run Ubuntu the IP address of Windows is dead (not active). If you run Windows the IP address of Ubuntu will be dead.

It is not about the IP address, but about the whole TCP-IP stack (programs) that are loaded by the OS. If the OS is not loaded the stack will not be loaded.

---

### Post by NRV on 2012-04-02
hey thanks for the replies :)

---

