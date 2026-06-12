---
title: "Ubuntu Server 20.04 does not launch minidlna server since upgrade to 20.04"
date: 2021-01-09
forum: Multimedia Software
---

### Post by ccor58 on 2021-01-09
I have run mindlna video media server for years on ubuntu server prior to 20.04LTS upgrade but have had little success since and no recent updates have come up with any solutions to enable it to run again that I can ascertain. When installed on a ubuntustudio w/s it can be configured and runs OK just not on ubuntu server.
Is there any specific reason for this or a fix to overcome whatever shortcomings there was on the upgrade that accidentally possibly prevents it now ?

Thanks

---

### Post by Tadaen_Sylvermane on 2021-01-09
Please post ```
systemctl status minidlna
```

I know nothing of Ubuntu Studio but this thread reminded me that I hadn't reinstalled it on my server when I did a fresh install to 20.04. I followed the Configuration Globally from [https://help.ubuntu.com/community/MiniDLNA](https://help.ubuntu.com/community/MiniDLNA). Restarted service and away it went. Make sure it's configured the same as needed.

---

### Post by ajgreeny on 2021-01-09
You may need to run the enable command prior to the start command and I think you need minidlna.service not just minidlna
```
systemctl enable minidlna.service
```
I have ***systemctl start minidlna.service*** as an alias (dlna+) as well as a stop alias  (dlna-) to quickly allow me to start and stop it should I need to.

EDIT:
Having just tried this out it appears that the word ***service*** is not needed for those commands; ***minidlna*** works when used alone.

---

