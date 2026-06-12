---
title: "can't connect to database- please help!"
date: 2012-10-17
forum: Mythbuntu
---

### Post by itlarson on 2012-10-17
I have a all in one 10.4 mythbox which suddenly can't connect to it's database.  It happened after a hang and reboot- now when the frontend starts I get the setup page.  Here are some of the messages it gives:

The "select your preferred language" page opens.  I select "English"
A message box appears, it says:
     No UPnP  (The only option to select is OK).  I select "OK"
The "Database configuration 1/2" page opens
     This is the info on the page:
     "Myth could not connect to the database.  Please verify your database setting below."
     The settings are as follows:
          Hostname: localhost
          Ping test server  is checked
         Database name:  mythconverg
         User:  mythtv
         Password:  <xxxxxxx>
         (All other fields are blank)
     If I click "Finish",
A message box appears, it says:
     Cannot find (ping) database  (The only option is to select "OK").  I select "OK"
The "Database configuration 1/2" page opens again.  The only way to get out of this loop is to select "Cancel" on the page.

Choice log excerpts:
2012-10-17 11:07:33.272 Empty LocalHostName.
2012-10-17 11:07:33.272 Using localhost value of jsl-sll1
2012-10-17 11:07:33.273 Testing network connectivity to 'localhost.'
................................................................................
2012-10-17 11:07:35.341 UPnPautoconf() - No UPnP backends found
2012-10-17 11:07:35.341 No UPnP backends found
2012-10-17 11:07:35.345 Primary screen: 0.
2012-10-17 11:07:35.346 Using screen 0, 1360x768 at 0,0
2012-10-17 11:07:35.346 Could not find theme:  - Switching to Terra
2012-10-17 11:07:35.348 Using theme base resolution of 1280x720
2012-10-17 11:07:35.378 Desktop video mode: 1360x768 59.9628 Hz
2012-10-17 11:07:35.404 get_ip: Name or service not known
2012-10-17 11:07:35.404 LIRC, Error: Failed to parse IP address ''
2012-10-17 11:07:35.404 JoystickMenuThread Error: Joystick disabled - Failed to read /home/jsl-sll/.mythtv/joystickmenurc
2012-10-17 11:07:35.420 New DB connection, total: 1
2012-10-17 11:07:35.439 Using Frameless Window
2012-10-17 11:07:35.439 Using Full Screen Window
2012-10-17 11:07:35.450 Using the Qt painter
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
<repeats about 12 times>
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
2012-10-17 11:08:07.074 User cancelled database configuration
2012-10-17 11:08:07.092 Failed to init MythContext, exiting.
2012-10-17 11:08:07.092 Deleting UPnP client...

That's the end of the log.  Could the database be corrupted from the ugly reboot?  Thanks for any help.

---

### Post by tgm4883 on 2012-10-17
is MySQL running?

---

### Post by itlarson on 2012-10-17
is pgrep mysql the best way to do that?

I also tried this based on what I found in the backend logs:
[http://www.mythtv.org/wiki/Troubleshooting:Mythbackend_will_not_start_after_upgrade]("http://www.mythtv.org/wiki/Troubleshooting:Mythbackend_will_not_start_after_upgrade")

---

### Post by tgm4883 on 2012-10-17
```
sudo service mysql status
```

---

### Post by itlarson on 2012-10-17
Ok- I fixed this somehow, if I figure out how, or what caused the problem in the first place, I'll post it here.  Thanks for the help.

---

