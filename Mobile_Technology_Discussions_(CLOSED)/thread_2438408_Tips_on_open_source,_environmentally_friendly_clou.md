---
title: "Tips on open source, environmentally friendly cloud storage"
date: 2020-03-11
forum: Mobile Technology Discussions (CLOSED)
---

### Post by lemino on 2020-03-11
Hello! I'm all in favor of open source and try to use it whenever possible. I'm also concerned about the environment and because of the current crisis with rising co2-levels try to lessen my dito footprint in the digital world. This my question; I've been using dropbox for a long time, but when I started to do a little research on how different tech companies handled the question of the climate, I found out that dropbox doesn't even have a policy on the issue. So I migrated my data and am now on Google drive, since they have a comparably good policy on reducing emissions etc. However, if there is an alternative that is about open source AND have a strong commitment to the environment (for example by only using renewable energy to power their servers), I would definitely go for that option instead. So far, I haven't been able to find anything along these lines, does anyone in here have any tips to provide?

---

### Post by TheFu on 2020-03-14
The only way to know the truth, all companies lie, is to run your own.  Google isn't exactly trustworthy.  They are good at convenience, but terrible at the things that really matter.

A home file access/sharing system doesn't need much power at all.  A raspberry pi v2 can do it.  That's less than 2a/5V and $40, one-time HW cost.  For $50, you get a faster Pi v4, but it uses more amps.
[https://pimylifeup.com/raspberry-pi-nextcloud-server/](https://pimylifeup.com/raspberry-pi-nextcloud-server/) says it is a beginner level project.
There are other possible solutions too. Seafile or even just plain ssh/scp/sftp/rsync/sshfs.  All linux file managers support sftp:// URLs, so secure access to your files at home from anywhere is pretty easy.  IMHO.

Ref:[LIST]
[*][https://slate.com/technology/2018/10/google-is-losing-users-trust.html](https://slate.com/technology/2018/10/google-is-losing-users-trust.html)
[*][https://www.forbes.com/sites/kateoflahertyuk/2018/10/10/this-is-why-people-no-longer-trust-google-and-facebook-with-their-data/](https://www.forbes.com/sites/kateoflahertyuk/2018/10/10/this-is-why-people-no-longer-trust-google-and-facebook-with-their-data/)
[*][https://medium.com/@guohuade/the-two-reasons-i-dont-trust-google-with-my-data-530a961e8ce8](https://medium.com/@guohuade/the-two-reasons-i-dont-trust-google-with-my-data-530a961e8ce8)
[*][https://www.theguardian.com/technology/2020/jan/03/google-executive-human-rights-activism](https://www.theguardian.com/technology/2020/jan/03/google-executive-human-rights-activism)
[*][https://www.inc.com/jason-aten/nest-just-sent-out-this-email-its-a-reminder-of-why-why-people-just-dont-trust-google.html](https://www.inc.com/jason-aten/nest-just-sent-out-this-email-its-a-reminder-of-why-why-people-just-dont-trust-google.html)
[/LIST]

---

### Post by lemino on 2020-03-15
Thanks TheFu for tips, I'll consider it and check it out! :) Good thing about running your own server is that you can easily choose how you wanna power it (by buying renewable energy for example).

---

