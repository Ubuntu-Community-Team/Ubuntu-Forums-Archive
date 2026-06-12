---
title: "ACPI: Myth backend not going through idle"
date: 2008-11-10
forum: Mythbuntu
---

### Post by cw1035 on 2008-11-10
I've set up a new system using Mythbuntu 8.04.1. When setting up ACPI support I discovered that when the system boots up normally the backend stops going through the idle mode check. If I restart the backend using "/etc/init.d/mythtv-backend restart" the system goes through the idle mode check without any problems until the system is rebooted. I tracked this down to line 585 in the attached backend log file, where (SHUTDOWN_COUNTDOWN -1) is asserted. Can anyone tell me what is causing this, and how to correct this? Thanks.
CW

---

### Post by majoridiot on 2008-11-10
> **cw1035 said:**
> I've set up a new system using Mythbuntu 8.04.1. When setting up ACPI support I discovered that when the system boots up normally the backend stops going through the idle mode check. If I restart the backend using "/etc/init.d/mythtv-backend restart" the system goes through the idle mode check without any problems until the system is rebooted. I tracked this down to line 585 in the attached backend log file, where (SHUTDOWN_COUNTDOWN -1) is asserted. Can anyone tell me what is causing this, and how to correct this? Thanks.
CW

did you check the shutdown/wakeup options page in 1. General in backend setup and make sure the
"Block shutdown before client connected" box is *unticked*?

---

### Post by cw1035 on 2008-11-10
> **majoridiot said:**
> did you check the shutdown/wakeup options page in 1. General in backend setup and make sure the
"Block shutdown before client connected" box is *unticked*?

Yes. Everything works correctly when the backend is restarted. The system goes through it's idle checks, and shuts down when appropriate. When the system is rebooted, it starts to work. You can see the "SHUTDOWN_COUNTDOWN" start from 60 (line 479), go to 50 (line 511), then 40 (line 550), then something happens and it goes to "-1" (line 581 & 585) which I believe is disable. After that, the "SHUTDOWN_COUNTDOWN" event is never seen again.

---

