---
title: "Apache2 won't start!"
date: 2010-10-23
forum: Networking &amp; Wireless
---

### Post by adamjkok on 2010-10-23
I restarted my box and noticed Apache2 wasn't running. When I ran the following command:

```
sudo /etc/init.d/apache2 start
```

I got the following error:

 * Starting web server apache2                                                  Action 'start' failed.
The Apache error log may have more information.
                                                                         [fail]

What should I do now?

---

### Post by kevinatkins on 2010-10-23
Please post your Apache configuration files - if Apache is failing to start it's usually a result of misconfiguration.

---

### Post by adamjkok on 2010-10-23
> **kevinatkins said:**
> Please post your Apache configuration files - if Apache is failing to start it's usually a result of misconfiguration.

Here's an archive of my entire /etc/apache2 directory. I installed it using the following tutorial: [http://bit.ly/cxW8gM](http://bit.ly/cxW8gM)

The only change I've made is I've added a virtual host through Webmin and edited httpd.conf to open the port (the local ISP blocks 80, and I just port-separate since entering a specific domain just causes problems).

---

### Post by lisati on 2010-10-23
Did you do as the error message suggested and look at the Apache2 error log?

---

