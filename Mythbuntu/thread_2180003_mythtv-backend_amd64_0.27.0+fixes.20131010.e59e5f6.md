---
title: "mythtv-backend amd64 0.27.0+fixes.20131010.e59e5f6 crashes, 20131008.756d95 does not"
date: 2013-10-10
forum: Mythbuntu
---

### Post by finn on 2013-10-10
Yesterday mythtv-backend and mythtv-backend-master both updated from version 20131008.756d95 to 20131010.e59e5f6 and as a result my master backend started having issues with the backend crashing and respawning repeatedly until the system stopped trying.

running the following commands to install the older versions of the backend packages solves the crashing with no other changes:
```

cd /var/cache/apt/archives 
sudo dpkg -i mythtv-backend_2%3a0.27.0+fixes.20131008.756d95d-0ubuntu0mythbuntu2_amd64.deb mythtv-backend-master_2%3a0.27.0+fixes.20131008.756d95d-0ubuntu0mythbuntu2_all.deb
sudo /etc/init.d/mythtv-backend start

```

my mythbackend log files when the backend crashes and respawns just say:
```
Oct 10 18:31:19 mythbox mythbackend: mythbackend[32574]: I ProcessRequest mainserver.cpp:1430 (HandleAnnounce) MainServer::ANN Monitor
Oct 10 18:31:19 mythbox mythbackend: mythbackend[32574]: I ProcessRequest mainserver.cpp:1432 (HandleAnnounce) adding: mythbox as a client (events: 0)
Oct 10 18:31:30 mythbox mythbackend: mythbackend[32574]: I TVRecEvent tv_rec.cpp:1565 (HandlePendingRecordings) TVRec[2]: ASK_RECORDING 2 28 0 0
Oct 10 18:31:30 mythbox mythbackend: mythbackend[32574]: I TVRecEvent tv_rec.cpp:1565 (HandlePendingRecordings) TVRec[1]: ASK_RECORDING 1 28 0 0
Oct 10 18:31:34 mythbox mythbackend: mythbackend[32574]: I CoreContext housekeeper.cpp:667 (Run) Queueing HouseKeeperTask 'RecordedArtworkUpdate'.
Oct 10 18:31:34 mythbox mythbackend: mythbackend[32574]: I HouseKeeping housekeeper.cpp:133 (Run) Running HouseKeeperTask 'RecordedArtworkUpdate'.
Oct 10 18:31:34 mythbox mythbackend: mythbackend[32574]: I HouseKeeping mythsystemunix.cpp:776 (Signal) Child PID 324 killed with Terminated
Oct 10 18:31:34 mythbox mythbackend: mythbackend[32574]: E HouseKeeping backendhousekeeper.cpp:470 (DoRun) Artwork command '/usr/bin/mythmetadatalookup' failed
Oct 10 18:31:34 mythbox mythbackend: mythbackend[32574]: I HouseKeeping housekeeper.cpp:137 (Run) HouseKeeperTask 'RecordedArtworkUpdate' Failed.
Oct 10 18:31:34 mythbox mythbackend: mythbackend[32574]: C CoreContext signalhandling.cpp:305 (handleSignal) Received Aborted: Code -6, PID 32574, UID 109, Value 0x00000000

```

dmesg gives this:
```
[   10.851003] RTL2832U usb_init_bulk_setting : USB2.0 HIGH SPEED (480Mb/s)
[   11.371943] init: plymouth-stop pre-start process (2528) terminated with status 1
[   12.236278] RTL2832U usb_init_bulk_setting : USB2.0 HIGH SPEED (480Mb/s)
[   13.170718] RTL2832U usb_init_bulk_setting : USB2.0 HIGH SPEED (480Mb/s)
[   76.119510] init: mythtv-backend main process (2303) killed by SEGV signal
[   76.119561] init: mythtv-backend main process ended, respawning
[   76.349518] RTL2832U usb_init_bulk_setting : USB2.0 HIGH SPEED (480Mb/s)
[   78.189423] RTL2832U usb_init_bulk_setting : USB2.0 HIGH SPEED (480Mb/s)
[   79.122076] RTL2832U usb_init_bulk_setting : USB2.0 HIGH SPEED (480Mb/s)
[  141.484689] init: mythtv-backend main process (3145) killed by ABRT signal
[  141.484739] init: mythtv-backend main process ended, respawning
[  141.715523] RTL2832U usb_init_bulk_setting : USB2.0 HIGH SPEED (480Mb/s)
[  142.660060] RTL2832U usb_init_bulk_setting : USB2.0 HIGH SPEED (480Mb/s)
[  144.520362] RTL2832U usb_init_bulk_setting : USB2.0 HIGH SPEED (480Mb/s)
[  145.457780] RTL2832U usb_init_bulk_setting : USB2.0 HIGH SPEED (480Mb/s)
[  208.875973] init: mythtv-backend main process (4476) killed by SEGV signal
[  208.876038] init: mythtv-backend respawning too fast, stopped

```

After downgrading to the older packages my backend works just fine.

---

### Post by finn on 2013-10-11
0.27.0+fixes.20131011.9bfed2b-0ubuntu0mythbuntu2 versions of both packages seem to be running fine now too.

---

