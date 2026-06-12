---
title: "How to reboot the router from command line"
date: 2011-07-23
forum: Networking &amp; Wireless
---

### Post by papaapa on 2011-07-23
Hello!

I need to reboot the router many times for technical reasons. But i don't want to d it manually from browser by going to 192.168.1.1.

I use Jdownloader to make a re-connection script with "reconnect recorder" which records every step which i did them from browser (192.168.1.1-interface of router). But JD can not record my every step. I don't know why :( 

Is there any way to reset router from command line?
(note: I did not see from web interface of router any telnet support.)

Thank you!

---

### Post by jmoorse on 2011-07-26
Most consumer grade routers do not have a CLI.  What make/model is your router?

---

### Post by 2F4U on 2011-07-26
I don't know what router you have, but all routers that I have owned did not provide me a way to access a command line/shell/terminal. Is there a special reason not to use the GUI reboot function?

---

### Post by papaapa on 2011-07-27
@jmoorse My router is tp-link wr741nd.

@2F4U For technically reasons i need to reset the router many times. That's why i can not do that always from GUI.

Jdownloader module use http-headers ( [http://web3mantra.com/wp-content/uploads/2011/05/Live-HTTP-Headers.jpg](http://web3mantra.com/wp-content/uploads/2011/05/Live-HTTP-Headers.jpg) ) to saves(records) all thinks that i done to reset from browser-GUI of router. But it can not just save the http header when i click reset button from gui. the other thinks can saved properly. Is there anyway like Jdownloaders module to save the http headers and execute them from command line (a script or anything...)?

---

