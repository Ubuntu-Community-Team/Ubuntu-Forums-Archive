---
title: "Best way to disable mythbuntu for testing DVB-S"
date: 2010-07-31
forum: Mythbuntu
---

### Post by delta_charlie on 2010-07-31
Hi all, I have a new install of mythbuntu 10.04 and I'm trying to test my SkyStar2 DVB-S card. I want to run tests from the terminal but it looks like the backend is grabbing the card. What is the best way to temporarily disable both the front and backends so I can boot direct into the desktop and access the terminal to run the tests?

Thanks, DC

---

### Post by roundhay on 2010-07-31
run this in the terminal

sudo /etc/init.d/mythtv-backend stop

and conversely

sudo /etc/init.d/mythtv-backend start

or

sudo /etc/init.d/mythtv-backend restart

---

### Post by nickrout on 2010-08-01
There is also a setting in the backend setup to only grab the card when myth wants to record - can't remember exacltly where, but it's easy to spot :)

---

### Post by delta_charlie on 2010-08-01
> **roundhay said:**
> run this in the terminal

sudo /etc/init.d/mythtv-backend stop

and conversely

sudo /etc/init.d/mythtv-backend start

or

sudo /etc/init.d/mythtv-backend restart

Hi, thanks for the info. The commands above sort of worked. Looks like Mythbuntu 10.04 has had an update. When I ran the command above the screen printed I should try: 

sudo service mythtv-backend stop

Got to run, DC

---

