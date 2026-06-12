---
title: "Mythbuntu TV tuning tables"
date: 2011-09-21
forum: Mythbuntu
---

### Post by tobiz on 2011-09-21
Where are the tuning tables located used by myth to tune to the TV channels? Now that the UK DVB-T switch over in my area is complete I need to retune mythbackend. I've used w_scan to get the transport data but I need to modify this since it returns some muxes I don't want to use (there for the wrong region in the opposite direction to the antenna is pointing). I can provide the transport data by hand but better to just set up the right table in the right place and let myth get on with it. Where is the table?

---

### Post by nickrout on 2011-09-23
```
select callsign,mplexid,serviceid from channel;
```

---

