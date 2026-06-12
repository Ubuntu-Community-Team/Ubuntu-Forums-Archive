---
title: "UK FreeView 7 FreeSat channel lineup sort?"
date: 2013-03-22
forum: Mythbuntu
---

### Post by drifting on 2013-03-22
Hi chaps.

Now had enough of manually sorting all the channels on Myth, was hoping to find some way to automate it.

Did a bit of googling and found a few scripts here and there for channel sorting, most seem to give dire warnings about using a later version of myth. I currrently run Mythbuntu 64 bit with the PPA enabled (Loads of updates of late so must be up to date .26) Have "Mythupchuk", but not yet dared to run it.

What I would like is a difinitive script that works with 12.04 and .26, last thing I want to do is mess up my database, did that once, took me ages to get all the years of programs back.

Regards Paul

---

### Post by jksj on 2013-03-23
I have a combined Freeview & Freesat system that used the xmltv feed from radio times to update the program listings. To do this you have to script the updates in order to keep the two sets of channels apart and maintain the xmltv ids. I have just moved back to using the broadcast EPG data but am keeping the script going to control the channel numbers. This level of scripting is pretty easy. So if you are confident enough with backing up and restoring the database I would go for it. (ask if your not sure how to do this - it is easy and does work)
To execute the script.
mysql -umythtv  -ppassword --database mythconverg < mythtv-retune-all.sql
Where password is the password in .mythtv/config.xml without a space after the -p
So the following sets all channels to invisible 
UPDATE channel SET visible=FALSE;
Then for each channel you want use a line like
UPDATE channel SET channum=1, visible=1, xmltvid="hd.bbc1.bbc.co.uk"  WHERE sourceid="1" AND serviceid="17540"; #'BBC One HD';
There is a sourceid for each tuner - you can check the value in Mythwebs channel info display. In my script the Freeview Tuner is souce 1 & Freesat 2 so remove the Freeview section and change sourcid appropriate to your system.
Remove the xmltv ids if you don't need them (with the preceeding comma)
So the above would be:-
UPDATE channel SET channum=1, visible=1  WHERE sourceid="1" AND serviceid="17540"; #'BBC One HD';
Serviceids can be found from any of the scripts you have looked at or from [http://en.kingofsat.net/freqs.php?&pos=28.2E&standard=All&ordre=freq&filtre=Clear](http://en.kingofsat.net/freqs.php?&pos=28.2E&standard=All&ordre=freq&filtre=Clear)
The lines at the bottom of the script turn off commercial flagging, assign all the channels which have not been set to a number from 60000 upwards and makes them invisible.
Paste the following into a file:-
UPDATE channel SET visible=FALSE;
-- Freeview
-- UPDATE channel SET channum=2,  visible=1, xmltvid="bbc2.bbc.co.uk"                          WHERE sourceid="1" AND serviceid="4287"; #'BBC 2';
UPDATE channel SET channum=1, visible=1, xmltvid="hd.bbc1.bbc.co.uk"                       WHERE sourceid="1" AND serviceid="17540"; #'BBC One HD';
UPDATE channel SET channum=2, visible=1, xmltvid="hd.bbc2.bbc.co.uk"                            WHERE sourceid="1" AND serviceid="17472"; #'BBC HD';
UPDATE channel SET channum=3, visible=1, xmltvid="hd.northwest-macro.itv1.itv.co.uk"         WHERE sourceid="1" AND serviceid="17608"; #'ITV 1 HD';
UPDATE channel SET channum=4, visible=1, xmltvid="hd.channel4.com"                         WHERE sourceid="1" AND serviceid="17664"; #'Channel 4 HD';
UPDATE channel SET channum=5,  visible=1, xmltvid="channel5.co.uk"                          WHERE sourceid="1" AND serviceid="8500"; #'Channel 5';
UPDATE channel SET channum=6,  visible=1, xmltvid="bbcthree.bbc.co.uk"                      WHERE sourceid="1" AND serviceid="4288"; #'BBC THREE';
UPDATE channel SET channum=7,  visible=1, xmltvid="bbcfour.bbc.co.uk"                       WHERE sourceid="1" AND serviceid="4544"; #'BBC FOUR';
UPDATE channel SET channum=12,  visible=1, xmltvid="dave.uktv.co.uk"                       WHERE sourceid="1" AND serviceid="22272"; #'Dave';
UPDATE channel SET channum=38,  visible=1, xmltvid="quest.discoveryeurope.com"              WHERE sourceid="1" AND serviceid="14498"; #'Quest';
UPDATE channel SET channum=80, visible=1, xmltvid="news.bbc.co.uk"                          WHERE sourceid="1" AND serviceid="4352"; #'BBC NEWS';
UPDATE channel SET channum=99, visible=1                                                    WHERE sourceid="1" AND serviceid="4416"; #'BBC Red Button';

-- Re-tune all FreeSat channels and set visible
-- Entertainment
UPDATE channel SET channum=101, visible=1, xmltvid="hd.bbc1.bbc.co.uk"                       WHERE sourceid="2" AND serviceid="6941"; #'BBC One HD';
-- UPDATE channel SET channum=101, visible=1, xmltvid="north-west.bbc1.bbc.co.uk"            WHERE sourceid="2" AND serviceid="6441"; #'BBC 1 North West';
UPDATE channel SET channum=102, visible=1, xmltvid="hd.bbc2.bbc.co.uk"                            WHERE sourceid="2" AND serviceid="6940"; #'BBC HD';
-- UPDATE channel SET channum=102, visible=1, xmltvid="bbc2.bbc.co.uk"                    WHERE sourceid="2" AND serviceid="6302"; #'BBC 2 England';
UPDATE channel SET channum=103, visible=1, xmltvid="hd.northwest-macro.itv1.itv.co.uk"       WHERE sourceid="2" AND serviceid="12130"; #'ITV1 HD';
-- UPDATE channel SET channum=103, visible=1, xmltvid="granada.itv1.itv.co.uk"  WHERE sourceid="2" AND serviceid="10080"; #'ITV 1 Granada';
UPDATE channel SET channum=104, visible=1, xmltvid="hd.channel4.com" WHERE sourceid="2" AND serviceid="21200"; #'Channel 4 HD';
-- UPDATE channel SET channum=104, visible=1, xmltvid="channel4.com"                            WHERE sourceid="2" AND serviceid="9214"; #'Channel 4 North';
UPDATE channel SET channum=105, visible=1, xmltvid="channel5.co.uk"                          WHERE sourceid="2" AND serviceid="7702"; #'Channel 5';
UPDATE channel SET channum=106, visible=1, xmltvid="bbcthree.bbc.co.uk"                      WHERE sourceid="2" AND serviceid="10351"; #'BBC THREE';
UPDATE channel SET channum=107, visible=1, xmltvid="bbcfour.bbc.co.uk"                       WHERE sourceid="2" AND serviceid="6316"; #'BBC FOUR';
-- UPDATE channel SET channum=109, visible=1, xmltvid="hd.bbc2.bbc.co.uk"                            WHERE sourceid="2" AND serviceid="6940"; #'BBC HD';
UPDATE channel SET channum=112, visible=1, xmltvid="tsod.plus-1.granada.itv1.itv.co.uk", recpriority=-1      WHERE sourceid="2" AND serviceid="10255"; #'ITV1+1';
UPDATE channel SET channum=113, visible=1, xmltvid="itv2.itv.co.uk"                          WHERE sourceid="2" AND serviceid="10070"; #'ITV2';
UPDATE channel SET channum=115, visible=1, xmltvid="itv3.itv.co.uk"                          WHERE sourceid="2" AND serviceid="10260"; #'ITV3';
UPDATE channel SET channum=117, visible=1, xmltvid="itv4.itv.co.uk"                          WHERE sourceid="2" AND serviceid="10072"; #'ITV4';

UPDATE channel SET channum=121, visible=1, xmltvid="tsod.plus-1.channel4.com", recpriority=-1                WHERE sourceid="2" AND serviceid="8311"; #'Channel 4+1';

UPDATE channel SET channum=122, visible=1, xmltvid="e4.channel4.com"                         WHERE sourceid="2" AND serviceid="8305"; #'E4';
UPDATE channel SET channum=124, visible=1, xmltvid="more4.channel4.com"                      WHERE sourceid="2" AND serviceid="8340"; #'More4';

UPDATE channel SET channum=128, visible=1, xmltvid="tsod.plus-1.channel5.co.uk", recpriority=-1              WHERE sourceid="2" AND serviceid="7720"; #'Channel 5+1';
UPDATE channel SET channum=129, visible=1, xmltvid="fiveusa.channel5.co.uk"                  WHERE sourceid="2" AND serviceid="7710"; #'fiveusa';
UPDATE channel SET channum=134, visible=1, xmltvid="drama.cbs.com"                           WHERE sourceid="2" AND serviceid="50903"; #'CBS Drama';
UPDATE channel SET channum=135, visible=1, xmltvid="reality.cbs.com"                         WHERE sourceid="2" AND serviceid="53275"; #'CBS Reality';
UPDATE channel SET channum=137, visible=1, xmltvid="action.cbs.com"                          WHERE sourceid="2" AND serviceid="52007"; #'CBS Action';
UPDATE channel SET channum=138, visible=1, xmltvid="horror.cbs.com"                          WHERE sourceid="2" AND serviceid="52105"; #'Horror Channel';
UPDATE channel SET channum=142, visible=1, xmltvid="entertainment.truemovies.tv"             WHERE sourceid="2" AND serviceid="53375"; #'True Ent';
UPDATE channel SET channum=143, visible=1                                                    WHERE sourceid="2" AND serviceid="54110"; #'Men & Movies';

-- News & Sport
UPDATE channel SET channum=200, visible=1, xmltvid="news.bbc.co.uk"                          WHERE sourceid="2" AND serviceid="6405"; #'BBC NEWS';
UPDATE channel SET channum=204, visible=1, xmltvid="euronews.com"                            WHERE sourceid="2" AND serviceid="55280"; #'Euronews';
UPDATE channel SET channum=205, visible=1                                                    WHERE sourceid="2" AND serviceid="52570"; #'France 24';
UPDATE channel SET channum=206, visible=1                                                    WHERE sourceid="2" AND serviceid="53148
"; #'RT HD'
UPDATE channel SET channum=207, visible=1, xmltvid="europe.cnn.com"                          WHERE sourceid="2" AND serviceid="7140"; #'CNN';
UPDATE channel SET channum=208, visible=1, xmltvid="bloomberg.com"                           WHERE sourceid="2" AND serviceid="52550"; #'Bloomberg';
UPDATE channel SET channum=209, visible=1, xmltvid="hd.world.nhk.or.jp"                       WHERE sourceid="2" AND serviceid="53147"; #'NHK World HD';
UPDATE channel SET channum=210, visible=1, xmltvid="europe.cnbc.com"                         WHERE sourceid="2" AND serviceid="52111"; #'CNBC';

-- Movies
UPDATE channel SET channum=300, visible=1, xmltvid="filmfour.channel4.com"                   WHERE sourceid="2" AND serviceid="9220"; #'Film4';
-- UPDATE channel SET channum=302, visible=1, xmltvid="1.truemovies.tv"                         WHERE sourceid="2" AND serviceid="53320"; #'True Movies 1';
-- UPDATE channel SET channum=303, visible=1, xmltvid="2.truemovies.tv"                         WHERE sourceid="2" AND serviceid="53325"; #'True Movies 2';
-- UPDATE channel SET channum=304, visible=1, xmltvid="1.movies4men.co.uk"                      WHERE sourceid="2" AND serviceid="51116"; #'Movies4Men';
-- UPDATE channel SET channum=304, visible=1, xmltvid="1.movies4men.co.uk"                      WHERE sourceid="2" AND serviceid="53109"; #'Movies4Men';
-- UPDATE channel SET channum=305, visible=1, xmltvid="tsod.plus-1.1.movies4men.co.uk"          WHERE sourceid="2" AND serviceid="51118"; #'Movies4Men +1';
-- UPDATE channel SET channum=306, visible=1, xmltvid="2.movies4men.co.uk"                      WHERE sourceid="2" AND serviceid="51117"; #'Movies4Men 2';
-- UPDATE channel SET channum=306, visible=1, xmltvid="2.movies4men.co.uk"                      WHERE sourceid="2" AND serviceid="53110"; #'Movies4Men 2';
-- UPDATE channel SET channum=307, visible=1, xmltvid="tsod.plus-1.2.movies4men.co.uk"          WHERE sourceid="2" AND serviceid="51119"; #'Movies4Men 2 +1';
-- UPDATE channel SET channum=307, visible=1, xmltvid="tsod.plus-1.2.movies4men.co.uk"          WHERE sourceid="2" AND serviceid="52121"; #'Movies4Men 2 +1';

-- Lifestyle
-- UPDATE channel SET channum=400, visible=1, xmltvid="weddingtv.com"                           WHERE sourceid="2" AND serviceid="53280"; #'Wedding TV';
-- UPDATE channel SET channum=402, visible=1, xmltvid="showcase.information.tv"                 WHERE sourceid="2" AND serviceid="50880"; #'Information TV';
-- UPDATE channel SET channum=403, visible=1, xmltvid="showcase.information.tv"                 WHERE sourceid="2" AND serviceid="52125"; #'Showcase';
UPDATE channel SET channum=405, visible=1, xmltvid="foodnetwork.com"                         WHERE sourceid="2" AND serviceid="53260"; #'Food Network';

-- Music
UPDATE channel SET channum=500, visible=1, xmltvid="chartshow.com"                           WHERE sourceid="2" AND serviceid="53365"; #'Chart Show TV';
-- UPDATE channel SET channum=501, visible=1                                                    WHERE sourceid="2" AND serviceid="53355"; #'The Vault';
UPDATE channel SET channum=502, visible=1, xmltvid="essentialflava.com"                      WHERE sourceid="2" AND serviceid="53300"; #'Flava';
UPDATE channel SET channum=503, visible=1, xmltvid="scuzz.tv"                                WHERE sourceid="2" AND serviceid="53310"; #'Scuzz';
-- UPDATE channel SET channum=504, visible=1, xmltvid="b4utv.com"                               WHERE sourceid="2" AND serviceid="52135"; #'B4U Music';
-- UPDATE channel SET channum=509, visible=1                                                    WHERE sourceid="2" AND serviceid="50470"; #'Zing';
-- UPDATE channel SET channum=514, visible=1                                                    WHERE sourceid="2" AND serviceid="50879"; #'Clubland TV';
-- UPDATE channel SET channum=515, visible=1                                                    WHERE sourceid="2" AND serviceid="55022"; #'Vintage TV';
-- UPDATE channel SET channum=516, visible=1                                                    WHERE name='NME TV';
-- UPDATE channel SET channum=517, visible=1, xmltvid="bliss.co.uk"                             WHERE sourceid="2" AND serviceid="53305"; #'Bliss';

-- Childrens
UPDATE channel SET channum=600, visible=1, xmltvid="cbbc.bbc.co.uk"                          WHERE sourceid="2" AND serviceid="6317"; #'CBBC Channel';
UPDATE channel SET channum=601, visible=1, xmltvid="cbeebies.bbc.co.uk"                      WHERE sourceid="2" AND serviceid="6418"; #'CBeebies';
UPDATE channel SET channum=602, visible=1, xmltvid="citv.itv.co.uk"                          WHERE sourceid="2" AND serviceid="10071"; #'CITV';
-- UPDATE channel SET channum=603, visible=1, xmltvid="popfun.co.uk"                            WHERE sourceid="2" AND serviceid="53340"; #'POP';
-- UPDATE channel SET channum=604, visible=1                                                    WHERE sourceid="2" AND serviceid="53360"; #'PopGirl';
-- UPDATE channel SET channum=605, visible=1, xmltvid="tinypop.com"                             WHERE sourceid="2" AND serviceid="53330"; #'Tiny Pop';
-- UPDATE channel SET channum=606, visible=1                                                    WHERE sourceid="2" AND serviceid="53350"; #'Kix!';

UPDATE channel SET channum=607, visible=1                                                       WHERE sourceid="2" AND serviceid="6390"; #'red button';
-- Mark turn off commercial flagging.
UPDATE channel set commmethod=-2;

-- Just to be Sure turn eit off for unused channels using visible as master.
UPDATE channel set useonairguide=FALSE WHERE visible=FALSE;
UPDATE channel set useonairguide=1 WHERE visible=1;
-- needs fixing properly
UPDATE channel SET channum=60000 WHERE visible=FALSE;
SELECT @n:=60000;
UPDATE channel SET channum=@n:=@n+1 WHERE visible=FALSE;

---

### Post by drifting on 2013-03-24
Thanks so much for such a comprehensive answer, will give this a bash later in the week when I get some time off. One question? Are you referring to running the mythupchuk script? As you mention "mythtv-retune-all.sql" where did that come from in the line :-
To execute the script.
mysql -umythtv -ppassword --database mythconverg < mythtv-retune-all.sql

Not that confident in any scripting, but try to backup prior to closing my eyes, crossing my fingers and pressing go.

Paul

---

### Post by jksj on 2013-03-25
High I will try to clarify but it is always difficult to figure out how much detail people need.
The core of this info comes from the wiki [http://www.mythtv.org/wiki/UK_Channel_Assignments](http://www.mythtv.org/wiki/UK_Channel_Assignments).
The method I proposed operates directly on the mythtv database which is frowned on as it is dependent on the internal structure and makes standard user support impossible. So only do this if you are happy to take responsibility into your own hands. 
Using mythupchuk would be safer (still unsupported) but at least not unique to you and may get updated for each version of Mythtv.
The method I proposed is actually much simpler but you must be happy to get in there with mysql. 
First force a database backup.
/usr/share/mythtv/mythconverg_backup.pl --verbose
Copy the text from the previous post below the line 
"Paste the following into a file:-"
into file mythtv-retune-all.sql
edit this to meet your requirements then run it using the instuctions above.


sudo stop mythtv-backend 
mysql -umythtv -ppassword --database mythconverg < mythtv-retune-all.sql
sudo start mythtv-backend 

Check the results are what you wanted on the Mythweb settings channel info page.
If it has all gone horably wrong - restore the database.
                        /usr/share/mythtv/mythconverg_restore.pl --drop_database --create_database --filename /var/lib/mythtv/db_backups/mythconverg ... the latest version of the database created by the backup.
Enjoy ...

---

