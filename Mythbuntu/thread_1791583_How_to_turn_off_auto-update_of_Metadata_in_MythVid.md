---
title: "How to turn off auto-update of Metadata in MythVideo?"
date: 2011-06-27
forum: Mythbuntu
---

### Post by JamesNorris on 2011-06-27
I have disabled the "perform metadata update after video scan" however it seems on a daily basis, my videos are being renamed by Myth. Is there another setting somewhere I need to disable?

I've checked through both my frontend and backend logs and can find no evidence of when it happens.

It is even renaming some of my videos into other languages!

---

### Post by nickrout on 2011-06-27
I think it is one of these three scripts:

```
/etc/cron.daily/mythvideo
/etc/cron.hourly/mythvideo
/etc/cron.weekly/mythvideo

```

---

### Post by JamesNorris on 2011-06-27
> **nickrout said:**
> I think it is one of these three scripts:

```
/etc/cron.daily/mythvideo
/etc/cron.hourly/mythvideo
/etc/cron.weekly/mythvideo

```

Thanks, I suspect it is the daily cron job. I've commented out all lines and I'll see if this does it.

---

### Post by JamesNorris on 2011-06-29
> **nickrout said:**
> I think it is one of these three scripts:

```
/etc/cron.daily/mythvideo
/etc/cron.hourly/mythvideo
/etc/cron.weekly/mythvideo

```


It was, indeed, the daily one, but I had to edit three scripts in the end, as it ran for the frontend and backend too.

---

