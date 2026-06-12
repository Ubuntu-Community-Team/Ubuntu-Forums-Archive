---
title: "DVB device not available at mythtv-backend startup"
date: 2012-03-22
forum: Mythbuntu
---

### Post by erangaj on 2012-03-22
Hi All,

I recently installed Mythbuntu 11.10. But the myth backend wasn't starting automatically. So added the below line to /etc/rc.local to start the mythtv-backend while booting.

```

start mythtv-backend start
exit 0

```

However, I cannot get live tv without manually restarting the backend. As per the mythbackend.log the DVB device (/dev/dvb/adapter0/frontend0) isn't available at mythbackend startup (file not found).

(I use an af9035 DVB-T (USB) device and followed this post to install the driver. [http://askubuntu.com/a/84611/48674]("http://askubuntu.com/a/84611/48674"))

Anyone have any ideas on how to fix the issue?

Thanks

---

### Post by nickrout on 2012-03-23
> **erangaj said:**
> Hi All,

I recently installed Mythbuntu 11.10. But the myth backend wasn't starting automatically. So added the below line to /etc/rc.local to start the mythtv-backend while booting.

```

start mythtv-backend start
exit 0

```

However, I cannot get live tv without manually restarting the backend. As per the mythbackend.log the DVB device (/dev/dvb/adapter0/frontend0) isn't available at mythbackend startup (file not found).

(I use an af9035 DVB-T (USB) device and followed this post to install the driver. [http://askubuntu.com/a/84611/48674]("http://askubuntu.com/a/84611/48674"))

Anyone have any ideas on how to fix the issue?

Thanks

Put a delay in your rc.local script, as it is probably taking some time for your tuner to be detected and the driver properly loading.

---

### Post by erangaj on 2012-03-26
nickrout,

Thanks for the tip. Finally solved by adding a script to delay  mythbackend and frontend until the DVB device is up.

---

### Post by nickrout on 2012-03-27
> **erangaj said:**
> nickrout,

Thanks for the tip. Finally solved by adding a script to delay  mythbackend and frontend until the DVB device is up.

that is the correct way to do it, a simple "pause" command is the quick and dirty way :)

---

