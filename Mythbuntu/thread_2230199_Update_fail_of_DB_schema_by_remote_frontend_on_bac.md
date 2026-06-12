---
title: "Update fail of DB schema by remote frontend on backend"
date: 2014-06-17
forum: Mythbuntu
---

### Post by hobie2 on 2014-06-17
I've recently upgraded my FE/BE machine from 0.22 to 0.24, it is now up and running no problem.  When I attempt to connect to that BE from a remote FE I get an error concerning updating of the database schema.  I suspect that the remote FE doesn't have the proper premissions in mysql to access the database, however the way Mythtv gives errors implies to me that it is try update the schema version of the BE database.  That doesn't seem right.

Here is a screenshot of the remote frontend error:
[ATTACH=CONFIG]254029[/ATTACH]

Here is the CLI showing mysql relavent entries:[INDENT]```

2014-06-17 21:14:18.393 Empty LocalHostName.
2014-06-17 21:14:18.393 Using localhost value of tesla
2014-06-17 21:14:18.393 Clearing Settings Cache.
2014-06-17 21:14:18.393 Testing network connectivity to '192.168.1.5'
2014-06-17 21:14:18.494 Clearing Settings Cache.
2014-06-17 21:14:18.505 New DB connection, total: 1
2014-06-17 21:14:18.507 Connected to database 'mythconverg' at host: 192.168.1.5
2014-06-17 21:14:18.513 Closing DB connection named 'DBManager0'
2014-06-17 21:14:18.513 Clearing Settings Cache.
2014-06-17 21:14:18.515 Connected to database 'mythconverg' at host: 192.168.1.5
2014-06-17 21:14:18.517 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'language' AND hostname = 'tesla' <<<< Returns 1 row(s)
2014-06-17 21:14:18.518 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'country' AND hostname = 'tesla' <<<< Returns 1 row(s)
2014-06-17 21:14:18.518 Current locale en_US
2014-06-17 21:14:18.518 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2014-06-17 21:14:18.520 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'freqtable' AND hostname = 'tesla' <<<< Returns 0 row(s)
2014-06-17 21:14:18.521 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'freqtable' AND hostname IS NULL <<<< Returns 1 row(s)
2014-06-17 21:14:18.523 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'iso639language0' AND hostname = 'tesla' <<<< Returns 0 row(s)
2014-06-17 21:14:18.524 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'iso639language0' AND hostname IS NULL <<<< Returns 1 row(s)
2014-06-17 21:14:18.526 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'iso639language1' AND hostname = 'tesla' <<<< Returns 0 row(s)
2014-06-17 21:14:18.527 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'iso639language1' AND hostname IS NULL <<<< Returns 1 row(s)
2014-06-17 21:14:18.528 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'tvformat' AND hostname = 'tesla' <<<< Returns 0 row(s)
2014-06-17 21:14:18.529 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'tvformat' AND hostname IS NULL <<<< Returns 1 row(s)
2014-06-17 21:14:18.531 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'vbiformat' AND hostname = 'tesla' <<<< Returns 0 row(s)
2014-06-17 21:14:18.532 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'vbiformat' AND hostname IS NULL <<<< Returns 1 row(s)
2014-06-17 21:14:18.533 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'country' AND hostname = 'tesla' <<<< Returns 1 row(s)
2014-06-17 21:14:18.534 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'dateformat' AND hostname = 'tesla' <<<< Returns 1 row(s)
2014-06-17 21:14:18.536 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'language' AND hostname = 'tesla' <<<< Returns 1 row(s)
2014-06-17 21:14:18.537 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'mytharchivedateformat' AND hostname = 'tesla' <<<< Returns 1 row(s)
2014-06-17 21:14:18.538 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'mytharchivetimeformat' AND hostname = 'tesla' <<<< Returns 1 row(s)
2014-06-17 21:14:18.539 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'mytharchivevideoformat' AND hostname = 'tesla' <<<< Returns 1 row(s)
2014-06-17 21:14:18.541 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'shortdateformat' AND hostname = 'tesla' <<<< Returns 1 row(s)
2014-06-17 21:14:18.542 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'timeformat' AND hostname = 'tesla' <<<< Returns 1 row(s)
2014-06-17 21:14:18.695 DPMS is active.
2014-06-17 21:14:18.697 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'runfrontendinwindow' AND hostname = 'tesla' <<<< Returns 1 row(s)
2014-06-17 21:14:18.699 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'guioffsetx' AND hostname = 'tesla' <<<< Returns 0 row(s)
2014-06-17 21:14:18.700 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'guioffsetx' AND hostname IS NULL <<<< Returns 0 row(s)
2014-06-17 21:14:18.701 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'guioffsety' AND hostname = 'tesla' <<<< Returns 0 row(s)
2014-06-17 21:14:18.702 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'guioffsety' AND hostname IS NULL <<<< Returns 0 row(s)
2014-06-17 21:14:18.704 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'guiresolution' AND hostname = 'tesla' <<<< Returns 0 row(s)
2014-06-17 21:14:18.705 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'guiresolution' AND hostname IS NULL <<<< Returns 0 row(s)
2014-06-17 21:14:18.706 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'guiwidth' AND hostname = 'tesla' <<<< Returns 0 row(s)
2014-06-17 21:14:18.707 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'guiwidth' AND hostname IS NULL <<<< Returns 0 row(s)
2014-06-17 21:14:18.708 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'guiheight' AND hostname = 'tesla' <<<< Returns 0 row(s)
2014-06-17 21:14:18.710 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'guiheight' AND hostname IS NULL <<<< Returns 0 row(s)
2014-06-17 21:14:18.716 Desktop video mode: 1366x768 59.790 Hz
2014-06-17 21:14:18.717 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'guividmoderesolution' AND hostname = 'tesla' <<<< Returns 1 row(s)
2014-06-17 21:14:18.718 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'guividmoderefreshrate' AND hostname = 'tesla' <<<< Returns 0 row(s)
2014-06-17 21:14:18.719 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'guividmoderefreshrate' AND hostname IS NULL <<<< Returns 0 row(s)
2014-06-17 21:14:18.721 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'guividmodeforceaspect' AND hostname = 'tesla' <<<< Returns 0 row(s)
2014-06-17 21:14:18.722 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'guividmodeforceaspect' AND hostname IS NULL <<<< Returns 0 row(s)
2014-06-17 21:14:18.724 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'displaysizeresolution' AND hostname = 'tesla' <<<< Returns 0 row(s)
2014-06-17 21:14:18.725 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'displaysizeresolution' AND hostname IS NULL <<<< Returns 0 row(s)
2014-06-17 21:14:18.727 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'displaysizewidth' AND hostname = 'tesla' <<<< Returns 0 row(s)
2014-06-17 21:14:18.728 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'displaysizewidth' AND hostname IS NULL <<<< Returns 0 row(s)
2014-06-17 21:14:18.729 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'displaysizeheight' AND hostname = 'tesla' <<<< Returns 0 row(s)
2014-06-17 21:14:18.731 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'displaysizeheight' AND hostname IS NULL <<<< Returns 0 row(s)
2014-06-17 21:14:18.732 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'tvvidmoderesolution' AND hostname = 'tesla' <<<< Returns 1 row(s)
2014-06-17 21:14:18.733 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'tvvidmoderefreshrate' AND hostname = 'tesla' <<<< Returns 1 row(s)
2014-06-17 21:14:18.734 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'tvvidmodeforceaspect' AND hostname = 'tesla' <<<< Returns 1 row(s)
2014-06-17 21:14:18.735 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'vidmoderesolution0' AND hostname = 'tesla' <<<< Returns 0 row(s)
2014-06-17 21:14:18.736 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'vidmoderesolution0' AND hostname IS NULL <<<< Returns 0 row(s)
2014-06-17 21:14:18.738 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'vidmodewidth0' AND hostname = 'tesla' <<<< Returns 0 row(s)
2014-06-17 21:14:18.739 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'vidmodewidth0' AND hostname IS NULL <<<< Returns 0 row(s)
2014-06-17 21:14:18.740 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'vidmodeheight0' AND hostname = 'tesla' <<<< Returns 0 row(s)
2014-06-17 21:14:18.741 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'vidmodeheight0' AND hostname IS NULL <<<< Returns 0 row(s)
2014-06-17 21:14:18.742 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'tvvidmoderesolution0' AND hostname = 'tesla' <<<< Returns 1 row(s)
2014-06-17 21:14:18.743 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'tvvidmoderefreshrate0' AND hostname = 'tesla' <<<< Returns 1 row(s)
2014-06-17 21:14:18.744 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'tvvidmodeforceaspect0' AND hostname = 'tesla' <<<< Returns 1 row(s)
2014-06-17 21:14:19.469 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'uiimagecachesize' AND hostname = 'tesla' <<<< Returns 0 row(s)
2014-06-17 21:14:19.470 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'uiimagecachesize' AND hostname IS NULL <<<< Returns 0 row(s)
2014-06-17 21:14:19.470 Enabling Settings Cache.
2014-06-17 21:14:19.470 Clearing Settings Cache.
2014-06-17 21:14:19.471 Enabled verbose msgs:  important general database
2014-06-17 21:14:19.472 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'lcdserverhost' AND hostname = 'tesla' <<<< Returns 0 row(s)
2014-06-17 21:14:19.473 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'lcdserverhost' AND hostname IS NULL <<<< Returns 0 row(s)
2014-06-17 21:14:19.475 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'lcdserverport' AND hostname = 'tesla' <<<< Returns 0 row(s)
2014-06-17 21:14:19.476 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'lcdserverport' AND hostname IS NULL <<<< Returns 0 row(s)
2014-06-17 21:14:19.477 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'lcdenable' AND hostname = 'tesla' <<<< Returns 1 row(s)
2014-06-17 21:14:19.478 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'language' AND hostname = 'tesla' <<<< Returns 1 row(s)
2014-06-17 21:14:19.479 Loading en_us translation for module mythfrontend
2014-06-17 21:14:19.480 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'theme' AND hostname = 'tesla' <<<< Returns 1 row(s)
2014-06-17 21:14:19.481 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'usevideomodes' AND hostname = 'tesla' <<<< Returns 1 row(s)
2014-06-17 21:14:19.483 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'runfrontendinwindow' AND hostname = 'tesla' <<<< Returns 1 row(s)
2014-06-17 21:14:19.485 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'guioffsetx' AND hostname = 'tesla' <<<< Returns 0 row(s)
2014-06-17 21:14:19.486 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'guioffsetx' AND hostname IS NULL <<<< Returns 0 row(s)
2014-06-17 21:14:19.487 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'guioffsety' AND hostname = 'tesla' <<<< Returns 0 row(s)
2014-06-17 21:14:19.489 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'guioffsety' AND hostname IS NULL <<<< Returns 0 row(s)
2014-06-17 21:14:19.490 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'guiresolution' AND hostname = 'tesla' <<<< Returns 0 row(s)
2014-06-17 21:14:19.491 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'guiresolution' AND hostname IS NULL <<<< Returns 0 row(s)
2014-06-17 21:14:19.492 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'guiwidth' AND hostname = 'tesla' <<<< Returns 0 row(s)
2014-06-17 21:14:19.494 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'guiwidth' AND hostname IS NULL <<<< Returns 0 row(s)
2014-06-17 21:14:19.495 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'guiheight' AND hostname = 'tesla' <<<< Returns 0 row(s)
2014-06-17 21:14:19.496 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'guiheight' AND hostname IS NULL <<<< Returns 0 row(s)
2014-06-17 21:14:19.498 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'menutheme' AND hostname = 'tesla' <<<< Returns 1 row(s)
2014-06-17 21:14:19.499 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'lircsocket' AND hostname = 'tesla' <<<< Returns 1 row(s)
2014-06-17 21:14:19.500 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'lirckeypressedapp' AND hostname = 'tesla' <<<< Returns 0 row(s)
2014-06-17 21:14:19.502 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'lirckeypressedapp' AND hostname IS NULL <<<< Returns 0 row(s)
2014-06-17 21:14:19.502 LIRC, Error: Failed to connect to Unix socket '/var/run/lirc/lircd'
            eno: No such file or directory (2)
2014-06-17 21:14:19.502 JoystickMenuThread: Joystick disabled - Failed to read /home/hobie/.mythtv/joystickmenurc
2014-06-17 21:14:19.503 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Global' AND action = 'UP' AND hostname = 'tesla' ; <<<< Returns 1 row(s)
2014-06-17 21:14:19.505 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Global' AND action = 'DOWN' AND hostname = 'tesla' ; <<<< Returns 1 row(s)
2014-06-17 21:14:19.506 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Global' AND action = 'LEFT' AND hostname = 'tesla' ; <<<< Returns 1 row(s)
2014-06-17 21:14:19.507 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Global' AND action = 'RIGHT' AND hostname = 'tesla' ; <<<< Returns 1 row(s)
2014-06-17 21:14:19.509 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Global' AND action = 'NEXT' AND hostname = 'tesla' ; <<<< Returns 1 row(s)
2014-06-17 21:14:19.510 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Global' AND action = 'PREVIOUS' AND hostname = 'tesla' ; <<<< Returns 1 row(s)
2014-06-17 21:14:19.511 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Global' AND action = 'SELECT' AND hostname = 'tesla' ; <<<< Returns 1 row(s)
2014-06-17 21:14:19.513 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Global' AND action = 'BACKSPACE' AND hostname = 'tesla' ; <<<< Returns 1 row(s)
2014-06-17 21:14:19.514 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Global' AND action = 'ESCAPE' AND hostname = 'tesla' ; <<<< Returns 1 row(s)
2014-06-17 21:14:19.515 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Global' AND action = 'MENU' AND hostname = 'tesla' ; <<<< Returns 1 row(s)
2014-06-17 21:14:19.517 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Global' AND action = 'INFO' AND hostname = 'tesla' ; <<<< Returns 1 row(s)
2014-06-17 21:14:19.518 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Global' AND action = 'DELETE' AND hostname = 'tesla' ; <<<< Returns 1 row(s)
2014-06-17 21:14:19.519 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Global' AND action = 'EDIT' AND hostname = 'tesla' ; <<<< Returns 1 row(s)
2014-06-17 21:14:19.521 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Global' AND action = 'PAGEUP' AND hostname = 'tesla' ; <<<< Returns 1 row(s)
2014-06-17 21:14:19.522 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Global' AND action = 'PAGEDOWN' AND hostname = 'tesla' ; <<<< Returns 1 row(s)
2014-06-17 21:14:19.523 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Global' AND action = 'PAGETOP' AND hostname = 'tesla' ; <<<< Returns 1 row(s)
2014-06-17 21:14:19.525 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Global' AND action = 'PAGEMIDDLE' AND hostname = 'tesla' ; <<<< Returns 1 row(s)
2014-06-17 21:14:19.526 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Global' AND action = 'PAGEBOTTOM' AND hostname = 'tesla' ; <<<< Returns 1 row(s)
2014-06-17 21:14:19.528 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Global' AND action = 'PREVVIEW' AND hostname = 'tesla' ; <<<< Returns 1 row(s)
2014-06-17 21:14:19.529 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Global' AND action = 'NEXTVIEW' AND hostname = 'tesla' ; <<<< Returns 1 row(s)
2014-06-17 21:14:19.530 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Global' AND action = 'HELP' AND hostname = 'tesla' ; <<<< Returns 1 row(s)
2014-06-17 21:14:19.532 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Global' AND action = 'EJECT' AND hostname = 'tesla' ; <<<< Returns 1 row(s)
2014-06-17 21:14:19.533 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Global' AND action = 'CUT' AND hostname = 'tesla' ; <<<< Returns 1 row(s)
2014-06-17 21:14:19.534 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Global' AND action = 'COPY' AND hostname = 'tesla' ; <<<< Returns 1 row(s)
2014-06-17 21:14:19.536 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Global' AND action = 'PASTE' AND hostname = 'tesla' ; <<<< Returns 1 row(s)
2014-06-17 21:14:19.537 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Global' AND action = '0' AND hostname = 'tesla' ; <<<< Returns 1 row(s)
2014-06-17 21:14:19.539 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Global' AND action = '1' AND hostname = 'tesla' ; <<<< Returns 1 row(s)
2014-06-17 21:14:19.540 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Global' AND action = '2' AND hostname = 'tesla' ; <<<< Returns 1 row(s)
2014-06-17 21:14:19.541 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Global' AND action = '3' AND hostname = 'tesla' ; <<<< Returns 1 row(s)
2014-06-17 21:14:19.542 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Global' AND action = '4' AND hostname = 'tesla' ; <<<< Returns 1 row(s)
2014-06-17 21:14:19.544 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Global' AND action = '5' AND hostname = 'tesla' ; <<<< Returns 1 row(s)
2014-06-17 21:14:19.545 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Global' AND action = '6' AND hostname = 'tesla' ; <<<< Returns 1 row(s)
2014-06-17 21:14:19.547 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Global' AND action = '7' AND hostname = 'tesla' ; <<<< Returns 1 row(s)
2014-06-17 21:14:19.548 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Global' AND action = '8' AND hostname = 'tesla' ; <<<< Returns 1 row(s)
2014-06-17 21:14:19.549 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Global' AND action = '9' AND hostname = 'tesla' ; <<<< Returns 1 row(s)
2014-06-17 21:14:19.550 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Global' AND action = 'SYSEVENT01' AND hostname = 'tesla' ; <<<< Returns 1 row(s)
2014-06-17 21:14:19.552 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Global' AND action = 'SYSEVENT02' AND hostname = 'tesla' ; <<<< Returns 1 row(s)
2014-06-17 21:14:19.553 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Global' AND action = 'SYSEVENT03' AND hostname = 'tesla' ; <<<< Returns 1 row(s)
2014-06-17 21:14:19.555 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Global' AND action = 'SYSEVENT04' AND hostname = 'tesla' ; <<<< Returns 1 row(s)
2014-06-17 21:14:19.556 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Global' AND action = 'SYSEVENT05' AND hostname = 'tesla' ; <<<< Returns 1 row(s)
2014-06-17 21:14:19.557 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Global' AND action = 'SYSEVENT06' AND hostname = 'tesla' ; <<<< Returns 1 row(s)
2014-06-17 21:14:19.558 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Global' AND action = 'SYSEVENT07' AND hostname = 'tesla' ; <<<< Returns 1 row(s)
2014-06-17 21:14:19.560 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Global' AND action = 'SYSEVENT08' AND hostname = 'tesla' ; <<<< Returns 1 row(s)
2014-06-17 21:14:19.561 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Global' AND action = 'SYSEVENT09' AND hostname = 'tesla' ; <<<< Returns 1 row(s)
2014-06-17 21:14:19.562 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Global' AND action = 'SYSEVENT10' AND hostname = 'tesla' ; <<<< Returns 1 row(s)
2014-06-17 21:14:19.564 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Browser' AND action = 'ZOOMIN' AND hostname = 'tesla' ; <<<< Returns 1 row(s)
2014-06-17 21:14:19.565 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Browser' AND action = 'ZOOMOUT' AND hostname = 'tesla' ; <<<< Returns 1 row(s)
2014-06-17 21:14:19.566 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Browser' AND action = 'TOGGLEINPUT' AND hostname = 'tesla' ; <<<< Returns 1 row(s)
2014-06-17 21:14:19.568 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Browser' AND action = 'MOUSEUP' AND hostname = 'tesla' ; <<<< Returns 1 row(s)
2014-06-17 21:14:19.569 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Browser' AND action = 'MOUSEDOWN' AND hostname = 'tesla' ; <<<< Returns 1 row(s)
2014-06-17 21:14:19.571 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Browser' AND action = 'MOUSELEFT' AND hostname = 'tesla' ; <<<< Returns 1 row(s)
2014-06-17 21:14:19.572 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Browser' AND action = 'MOUSERIGHT' AND hostname = 'tesla' ; <<<< Returns 1 row(s)
2014-06-17 21:14:19.573 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Browser' AND action = 'MOUSELEFTBUTTON' AND hostname = 'tesla' ; <<<< Returns 1 row(s)
2014-06-17 21:14:19.575 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Browser' AND action = 'PAGEDOWN' AND hostname = 'tesla' ; <<<< Returns 1 row(s)
2014-06-17 21:14:19.576 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Browser' AND action = 'PAGEUP' AND hostname = 'tesla' ; <<<< Returns 1 row(s)
2014-06-17 21:14:19.577 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Browser' AND action = 'PAGELEFT' AND hostname = 'tesla' ; <<<< Returns 1 row(s)
2014-06-17 21:14:19.579 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Browser' AND action = 'PAGERIGHT' AND hostname = 'tesla' ; <<<< Returns 1 row(s)
2014-06-17 21:14:19.580 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Browser' AND action = 'NEXTLINK' AND hostname = 'tesla' ; <<<< Returns 1 row(s)
2014-06-17 21:14:19.581 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Browser' AND action = 'PREVIOUSLINK' AND hostname = 'tesla' ; <<<< Returns 1 row(s)
2014-06-17 21:14:19.583 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Browser' AND action = 'FOLLOWLINK' AND hostname = 'tesla' ; <<<< Returns 1 row(s)
2014-06-17 21:14:19.584 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Browser' AND action = 'HISTORYBACK' AND hostname = 'tesla' ; <<<< Returns 1 row(s)
2014-06-17 21:14:19.585 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Browser' AND action = 'HISTORYFORWARD' AND hostname = 'tesla' ; <<<< Returns 1 row(s)
2014-06-17 21:14:19.587 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Main Menu' AND action = 'EXIT' AND hostname = 'tesla' ; <<<< Returns 1 row(s)
2014-06-17 21:14:19.599 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'hidemousecursor' AND hostname = 'tesla' <<<< Returns 1 row(s)
2014-06-17 21:14:19.600 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'guioffsetx' AND hostname = 'tesla' <<<< Returns 0 row(s)
2014-06-17 21:14:19.601 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'guioffsetx' AND hostname IS NULL <<<< Returns 0 row(s)
2014-06-17 21:14:19.602 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'guioffsety' AND hostname = 'tesla' <<<< Returns 0 row(s)
2014-06-17 21:14:19.604 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'guioffsety' AND hostname IS NULL <<<< Returns 0 row(s)
2014-06-17 21:14:19.604 Using Frameless Window
2014-06-17 21:14:19.604 Using Full Screen Window
2014-06-17 21:14:19.755 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'themepainter' AND hostname = 'tesla' <<<< Returns 1 row(s)
2014-06-17 21:14:19.755 Using the Qt painter
2014-06-17 21:14:20.076 Disabling Settings Cache.
2014-06-17 21:14:20.076 Clearing Settings Cache.
2014-06-17 21:14:20.076 New DB connection, total: 2
2014-06-17 21:14:20.078 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'dbschemaautoupgrade' AND hostname = 'tesla' <<<< Returns 0 row(s)
2014-06-17 21:14:20.078 Connected to database 'mythconverg' at host: 192.168.1.5
2014-06-17 21:14:20.079 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'dbschemaautoupgrade' AND hostname IS NULL <<<< Returns 0 row(s)
2014-06-17 21:14:20.079 MSqlQuery::exec(DBManager1) SELECT data FROM settings WHERE value = 'theme' AND hostname = 'tesla' <<<< Returns 1 row(s)
2014-06-17 21:14:20.080 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'dbschemaver' AND hostname = 'tesla' <<<< Returns 0 row(s)
2014-06-17 21:14:20.081 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'dbschemaver' AND hostname IS NULL <<<< Returns 1 row(s)
2014-06-17 21:14:20.082 Current MythTV Schema Version (DBSchemaVer): 1317
2014-06-17 21:14:20.082 Not allowed to upgrade the database.
2014-06-17 21:14:20.102 MSqlQuery::exec(DBManager1) SELECT data FROM settings WHERE value = 'dbmsversionoverride' AND hostname = 'tesla' <<<< Returns 0 row(s)
2014-06-17 21:14:20.103 MSqlQuery::exec(DBManager1) SELECT data FROM settings WHERE value = 'dbmsversionoverride' AND hostname IS NULL <<<< Returns 0 row(s)
2014-06-17 21:14:20.104 MSqlQuery::exec(DBManager0) SELECT VERSION(); <<<< Returns 1 row(s)
2014-06-17 21:14:20.106 MSqlQuery::exec(DBManager1) SELECT data FROM settings WHERE value = 'usearrowaccels' AND hostname = 'tesla' <<<< Returns 1 row(s)
2014-06-17 21:14:20.108 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'popupheightpadding' AND hostname = 'tesla' <<<< Returns 0 row(s)
2014-06-17 21:14:20.109 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'popupheightpadding' AND hostname IS NULL <<<< Returns 0 row(s)
2014-06-17 21:14:20.110 MSqlQuery::exec(DBManager1) SELECT data FROM settings WHERE value = 'popupwidthpadding' AND hostname = 'tesla' <<<< Returns 0 row(s)
2014-06-17 21:14:20.112 MSqlQuery::exec(DBManager1) SELECT data FROM settings WHERE value = 'popupwidthpadding' AND hostname IS NULL <<<< Returns 0 row(s)
2014-06-17 21:14:21.835 Couldn't upgrade database to new schema, exiting.
2014-06-17 21:14:21.835 Deleting UPnP client...
2014-06-17 21:14:23.448 Destroying MythDBPrivate

```
[/INDENT]

And the mythfrontend.log info:[INDENT]```

2014-06-17 20:05:36.353 Empty LocalHostName.
2014-06-17 20:05:36.353 Using localhost value of tesla
2014-06-17 20:05:36.354 Testing network connectivity to '192.168.1.5'
2014-06-17 20:05:36.467 New DB connection, total: 1
2014-06-17 20:05:36.470 Connected to database 'mythconverg' at host: 192.168.1.5
2014-06-17 20:05:36.477 Closing DB connection named 'DBManager0'
2014-06-17 20:05:36.479 Connected to database 'mythconverg' at host: 192.168.1.5
2014-06-17 20:05:36.482 Current locale en_US
2014-06-17 20:05:36.482 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2014-06-17 20:05:36.656 DPMS is active.
2014-06-17 20:05:36.677 Desktop video mode: 1366x768 59.790 Hz
2014-06-17 20:05:37.443 Enabled verbose msgs:  important general
2014-06-17 20:05:37.451 Loading en_us translation for module mythfrontend
2014-06-17 20:05:37.473 LIRC, Error: Failed to connect to Unix socket '/var/run/lirc/lircd'
            eno: No such file or directory (2)
2014-06-17 20:05:37.474 JoystickMenuThread: Joystick disabled - Failed to read /home/hobie/.mythtv/joystickmenurc
2014-06-17 20:05:37.570 Using Frameless Window
2014-06-17 20:05:37.570 Using Full Screen Window
2014-06-17 20:05:37.698 Using the Qt painter
2014-06-17 20:05:37.913 New DB connection, total: 2
2014-06-17 20:05:37.914 New DB connection, total: 3
2014-06-17 20:05:37.916 New DB connection, total: 4
2014-06-17 20:05:37.917 Connected to database 'mythconverg' at host: 192.168.1.5
2014-06-17 20:05:37.917 Current MythTV Schema Version (DBSchemaVer): 1317
2014-06-17 20:05:37.917 Not allowed to upgrade the database.
2014-06-17 20:05:37.919 Connected to database 'mythconverg' at host: 192.168.1.5
2014-06-17 20:05:37.919 Connected to database 'mythconverg' at host: 192.168.1.5
2014-06-17 20:09:09.585 Couldn't upgrade database to new schema, exiting.
2014-06-17 20:09:09.585 Deleting UPnP client...

```
[/INDENT]

Since the remote FE doesn't run mysql, it must be referring to the BE, but I don't want the BE schema to be upgraded by the remote FE.  Am I missing something?

Thanks in advance.

---

### Post by blm-ubunet on 2014-06-18
Before updates:
- read the release notes (for each step)
[http://www.mythtv.org/wiki/Release_Notes_-_0.24](http://www.mythtv.org/wiki/Release_Notes_-_0.24)
- make a dB backup

After any updates you should first run:
- stop any FEs
- stop all BEs & MBEs
- run mythtv-setup
- wait for schema update 

mythtv-setup will create the new "config.xml" file (mysql.txt is deprecated).

The change from 0.22 to 0.24 probably requires timezone updates to mysql. (update: >= 0.26 requires this)
Might have to install mythplugins package to complete this.

---

### Post by hobie2 on 2014-06-18
Thanks for the reply blm-ubunet

I erred in my original post, I upgraded to version 0.27 on my combined FE/BE machine, and I did backup the DB before and then restored it after the upgrade.  At that time it did update the schema.  Checking the BE logs I see my current schema is 1317, which is referred to in that error message.  I'm happy with the FE/BE machine.  It's a different remote FE that seems to want to upgrade the DB.  What I'm trying to get at is that a local DB that it's trying to upgrade or is that the BE DB which is already upgraded to the proper schema?  I'll check to make sure the remote FE has the mythplugins package when I can.

---

### Post by blm-ubunet on 2014-06-18
Without using obscure compile options...all the FE & BE must be running the same schema version.

You should use mythtv-setup on the MBE to do schema updates..
IIRC There are (& historically were) minor schema changes in other plugin packages that only trigger if they are 
installed.
Does the MBE & (combined) FE have the mythplugins installed.
Actually I'm not so sure mythplugins is a separate package (anymore) that can be un-installed...

I can't tell from your logs (both from same remote FE ??) if it really is a remote FE..
Have you trimmed off the start?
I can't tell if the IP address of the remote FE is different to MBE..

Can you comfirm the MBE IP='192.168.1.5'?
What is the IP of the remote FE?

---

### Post by hobie2 on 2014-06-18
The remote FE was at 192.168.1.213, it is physically different machine located in my basement.  It doesn't look like the FE/MBE has 'mythplugins' installed, at least apt gives me the option to install the 'mythplugins' package.

What I should do is just backup mythconverg, double check the proper privileges are present for mythconverg on the MBE mysql setup, and then connect and see what happens.  If I don't like it I can always restore the backup copy.  It's just that it is the middle of the World Cup and I'm worried I'll make some larger mistake that I won't be able to recover from.

Thanks for the help so far.

---

### Post by blm-ubunet on 2014-06-19
Once mythtv-setup has been run on the MBE (or that combined FE is happy) then there shouldn't be anything important in the schema update.
Just bits related to plugins (music etc).
The music plugin only runs on a FE (& if installed)..

The remote FE just shouldn't be able to do any upgrade if you select no.

Stop the MBE & all/any BE/FEs.  (sudo service mythtv-backend stop)
Make a dB backup
install mythplugins
run mythtv-setup   on the MBE (just exit out from main menu** after** waiting > 2min for any update messages)
restart MBE

---

### Post by Patricia_Konarski_ on 2014-06-23
So, this is a pretty tricky situation.  I agree with BLM-ubunet's next move, but I would emphasize you want to exit out of the main menu for sure when doing it.  (If you have the same problem, you'll be able to discount the main menu presence as a contributing cause.)  All the best.

Patricia Konarski Tucson
--Freelance editor and owner of Patricia Konarski Literary Services of Tucson

---

