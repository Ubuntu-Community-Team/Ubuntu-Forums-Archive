---
title: "Mythbuntu: Strange mythwelcome screen behaviour"
date: 2008-08-02
forum: Mythbuntu
---

### Post by schitthoch2 on 2008-08-02
Hi,

I installed the mythbuntu 8.04.1 distribution on a friends PC. She uses it mainly for recording TV now and then. It is a combined BE/FE box. So it is important that the mythwelcome functionality is fully given to save energy using ACPI wakeup while keeping the timer recording features of mythtv.

As i am an experienced Mythtv user on Gentoo (>5 years), i could set up all necessary parameters easily (well done devs!). Then i changed the default startup from mythfrontend to mythwelcome by editing /etc/mythtv/settings.

The functionality of mythwelcome is provided then, all is working as it should except the mythwelcome screen.

From Gentoo i am familiar with the following behaviour i regard as very usefull:
- Mythwelcome detects if the box was powered by manual intervention (Pressing the power button) or automatically by an ACPI (or NVRAM) wakeup
- If an automatic wakeup happened (Timer programmed Recording), the box displays the mythwelcome screen showing what it is recording currently. When finished it counts down the set idle time and then shuts down, but still lets you start the frontend. If closing the frontend again mythwelcome reapears. This behaviour is fully supported by my mythbuntu installation.
- If a manual start is initiated, mythwelcome starts, but immediately starts the frontend, as a manual start means you want to make use of the frontend. If you shut down the frontend, the mythwelcome screen appears and counts down the idle time after finishing all underlying backend threats. After shutting down the frontend in mythbuntu, mythwelcome does show up only for a 1/3 second and vanishes. Then the XFCE desktop is showed. This leads to the following problem:
- Your box is still recording a show, while you shut down the frontend. An hour later you return to watch something, the box is still recording showing the XFCE desktop. So you now have to manually start the frontend using the XFCE App Menu. This is annoying as it is the only reason to have a keyboard/mouse plugged in the box. Everything else is working using a LIRC remote.

I already had this problem when i once tested mythbuntu 7.XX. It made me prefer other distros, although on the functionality/easiness i really do like mythbuntu. 

How can i resolve it?

Greetings 

Chris

---

### Post by schitthoch2 on 2008-08-18
up u go !

Someone please! If you need other information plz ask?

---

### Post by piousp on 2008-08-18
Sorry man, i just dont know how to help you, but lets try to give this thread some live bumping it.
Thats all i can do for you.
Good luck with it!

---

