---
title: "UK Freesat setup no tv schedules vie EIT"
date: 2012-02-12
forum: Mythbuntu
---

### Post by trippy21 on 2012-02-12
I have been setting up my Mythbuntu box for a few weeks now and had been struggling with the Channel setup. But after some time reading up about SQL i used this script which i modified from the mythtv wiki for a freesat install. 
 
 -- run mythfilldatabase after you have made these changes.
use mythconverg
UPDATE channel SET channum = channum+100000, visible=FALSE;
-- Entertainment
update channel SET channum=101 WHERE name='BBC 1 S West';
update channel SET channum=102 WHERE name='BBC 2 England';
update channel SET channum=103 WHERE name='ITV1 W Country';
update channel SET channum=104 WHERE name='Channel 4';
update channel SET channum=105 WHERE name='Channel 5';
update channel SET channum=106 WHERE name='BBC THREE';
update channel SET channum=107 WHERE name='BBC FOUR';
update channel SET channum=108 WHERE name='BBC One HD';
update channel SET channum=109 WHERE name='BBC HD';
update channel SET channum=110 WHERE name='BBC ALBA';
update channel SET channum=112 WHERE name='ITV1+1';
update channel SET channum=113 WHERE name='ITV2';
update channel SET channum=114 WHERE name='ITV2+1';
update channel SET channum=115 WHERE name='ITV3';
update channel SET channum=116 WHERE name='ITV3+1';
update channel SET channum=117 WHERE name='ITV4';
update channel SET channum=118 WHERE name='ITV4+1';
update channel SET channum=119 WHERE name='ITV1 HD';
update channel SET channum=120 WHERE name='S4C';
update channel SET channum=121 WHERE name='Channel 4 +1';
update channel SET channum=122 WHERE name='E4';
update channel SET channum=123 WHERE name='E4+1';
update channel SET channum=124 WHERE name='More4';
update channel SET channum=125 WHERE name='More4 +1';
update channel SET channum=126 WHERE name='Channel 4 HD';
update channel SET channum=128 WHERE name='Channel 5+1';
update channel SET channum=129 WHERE name='5 USA';
update channel SET channum=130 WHERE name='5 USA +1';
update channel SET channum=131 WHERE name='5*';
update channel SET channum=132 WHERE name='5* +1';
update channel SET channum=134 WHERE name='CBS Drama';
update channel SET channum=135 WHERE name='CBS Reality';
update channel SET channum=136 WHERE name='CBS Reality+1';
update channel SET channum=137 WHERE name='CBS Action';
update channel SET channum=138 WHERE name='horror channel';
update channel SET channum=139 WHERE name='horror ch+1';
update channel SET channum=140 WHERE name='BET';
update channel SET channum=141 WHERE name='BET +1';
update channel SET channum=142 WHERE name='True Ent';
update channel SET channum=143 WHERE name='Men & Movies';
-- News & Sport
update channel SET channum=200 WHERE name='BBC NEWS';
update channel SET channum=201 WHERE name='BBC PARLMNT';
update channel SET channum=203 WHERE name='Al Jazeera Eng';
update channel SET channum=204 WHERE name='Euronews';
update channel SET channum=205 WHERE name='France 24';
update channel SET channum=206 WHERE name='Russia Today';
update channel SET channum=207 WHERE name='CNN';
update channel SET channum=208 WHERE name='Bloomberg';
update channel SET channum=209 WHERE name='NHK World HD';
update channel SET channum=210 WHERE name='CNBC';
update channel SET channum=211 WHERE name='CCTV News';
update channel SET channum=298 WHERE name='Sky News';
update channel SET channum=299 WHERE name='NHK World TV';
-- Movies
update channel SET channum=300 WHERE name='Film4';
update channel SET channum=301 WHERE name='Film4 +1';
update channel SET channum=302 WHERE name='True Movies 1';
update channel SET channum=303 WHERE name='True Movies 2';
update channel SET channum=304 WHERE name='movies4men';
update channel SET channum=305 WHERE name='mov4men+1';
update channel SET channum=306 WHERE name='movies4men 2';
update channel SET channum=307 WHERE name='mov4men2 +1';
update channel SET channum=308 WHERE name='UMP Movies';
-- Lifestyle
update channel SET channum=400 WHERE name='wedding tv';
update channel SET channum=402 WHERE name='Information TV';
update channel SET channum=403 WHERE name='Showcase';
update channel SET channum=405 WHERE name='Food Network';
update channel SET channum=406 WHERE name='Food Netwrk+1';
-- Music
update channel SET channum=500 WHERE name='Chart Show TV';
update channel SET channum=501 WHERE name='The Vault';
update channel SET channum=502 WHERE name='Flava';
update channel SET channum=503 WHERE name='Scuzz';
update channel SET channum=504 WHERE name='B4U Music';
update channel SET channum=509 WHERE name='Zing';
update channel SET channum=514 WHERE name='Clubland TV';
update channel SET channum=515 WHERE name='Vintage TV';
update channel SET channum=516 WHERE name='Chart Show+1';
update channel SET channum=517 WHERE name='Bliss';
update channel SET channum=518 WHERE name='Massive R&B';
update channel SET channum=598 WHERE name='DanceNationTV';
update channel SET channum=599 WHERE name='WTF';
-- Childrens
update channel SET channum=600 WHERE name='CBBC Channel';
update channel SET channum=601 WHERE name='CBeebies';
update channel SET channum=602 WHERE name='CITV';
update channel SET channum=603 WHERE name='POP';
update channel SET channum=604 WHERE name='PopGirl';
update channel SET channum=605 WHERE name='Tiny Pop';
update channel SET channum=606 WHERE name='Kix!';
-- Special Interest
update channel SET channum=650 WHERE name='OceanFinance';
update channel SET channum=651 WHERE name='Renault TV';
update channel SET channum=652 WHERE name='Psychic TV';
update channel SET channum=690 WHERE name='Inspiration';
update channel SET channum=691 WHERE name='DAYSTAR';
update channel SET channum=692 WHERE name='revelation';
update channel SET channum=693 WHERE name='Islam Channel';
update channel SET channum=694 WHERE name='GOD Channel';
update channel SET channum=695 WHERE name='Sonlife';
-- Radio
update channel SET channum=700 WHERE name='BBC R1';
update channel SET channum=701 WHERE name='BBC R1X';
update channel SET channum=702 WHERE name='BBC R2';
update channel SET channum=703 WHERE name='BBC R3';
update channel SET channum=704 WHERE name='BBC R4 FM';
update channel SET channum=705 WHERE name='BBC R5L';
update channel SET channum=706 WHERE name='BBC R5SX';
update channel SET channum=707 WHERE name='BBC 6 Music';
update channel SET channum=708 WHERE name='BBC R4 Ex';
update channel SET channum=709 WHERE name='BBC Asian';
update channel SET channum=710 WHERE name='BBC R4 LW';
update channel SET channum=711 WHERE name='BBC WS';
update channel SET channum=712 WHERE name='BBC R Scot.';
update channel SET channum=713 WHERE name='BBC R n Gael';
update channel SET channum=714 WHERE name='BBC R Wales';
update channel SET channum=715 WHERE name='BBC R Cymru';
update channel SET channum=716 WHERE name='BBC R Ulster';
update channel SET channum=718 WHERE name='BBC London';
update channel SET channum=719 WHERE name='Capital FM';
update channel SET channum=720 WHERE name='Choice FM';
update channel SET channum=721 WHERE name='Classic FM';
update channel SET channum=722 WHERE name='Gold';
update channel SET channum=723 WHERE name='XFM';
update channel SET channum=724 WHERE name='Absolute';
update channel SET channum=725 WHERE name='Absolute CR';
update channel SET channum=726 WHERE name='Absolute80s';
update channel SET channum=727 WHERE name='NME';
update channel SET channum=728 WHERE name='WRN Europe';
update channel SET channum=729 WHERE name='Jazz FM';
update channel SET channum=730 WHERE name='Planet Rock';
update channel SET channum=731 WHERE name='TalkSport';
update channel SET channum=732 WHERE name='Smooth';
update channel SET channum=733 WHERE name='Heart';
update channel SET channum=750 WHERE name='RTE Radio 1';
update channel SET channum=751 WHERE name='RTE 2FM';
update channel SET channum=752 WHERE name='RTE Lyric fm';
update channel SET channum=753 WHERE name='RTE R na G';
update channel SET channum=777 WHERE name='InsightRadio';
update channel SET channum=786 WHERE name='BFBS Radio';
update channel SET channum=790 WHERE name='TWR';
update channel SET channum=799 WHERE name='Abs Rad 90s';
-- Shopping
update channel SET channum=800 WHERE name='QVC';
update channel SET channum=801 WHERE name='price-drop tv';
update channel SET channum=802 WHERE name='bid tv';
update channel SET channum=803 WHERE name='Pitch TV';
update channel SET channum=804 WHERE name='Pitch World';
update channel SET channum=805 WHERE name='Gems TV';
update channel SET channum=806 WHERE name='TV SHOP';
update channel SET channum=807 WHERE name='Jewelry Maker';
update channel SET channum=808 WHERE name='JML Direct';
update channel SET channum=809 WHERE name='JML Cookshop';
update channel SET channum=810 WHERE name='Ideal Extra';
update channel SET channum=812 WHERE name='Ideal World';
update channel SET channum=813 WHERE name='Create & Craft';
update channel SET channum=814 WHERE name='speed auction';
update channel SET channum=815 WHERE name='Jewellery Ch.';
update channel SET channum=816 WHERE name='QVC Beauty';
update channel SET channum=817 WHERE name='Rocks & Co 1';
update channel SET channum=818 WHERE name='Gems TV Extra';
update channel SET channum=819 WHERE name='Argos TV';
-- Gaming&Dating
-- Adult
update channel SET channum=870 WHERE name='Babestation';
update channel SET channum=875 WHERE name='PlayboyTV Chat';
-- Regional 
update channel SET channum=950 WHERE name='BBC 1 London';
update channel SET channum=951 WHERE name='BBC 1 CI';
update channel SET channum=952 WHERE name='BBC 1 E Mids';
update channel SET channum=953 WHERE name='BBC 1 East (E)';
update channel SET channum=954 WHERE name='BBC 1 East (W)';
update channel SET channum=955 WHERE name='BBC 1 N West';
update channel SET channum=956 WHERE name='BBC 1 NE & C';
update channel SET channum=957 WHERE name='BBC 1 NI';
update channel SET channum=958 WHERE name='BBC 1 Oxford';
update channel SET channum=959 WHERE name='BBC 1 S East';
update channel SET channum=960 WHERE name='BBC 1 Scotland';
update channel SET channum=961 WHERE name='BBC 1 South';
update channel SET channum=963 WHERE name='BBC 1 W Mids';
update channel SET channum=964 WHERE name='BBC 1 Wales';
update channel SET channum=965 WHERE name='BBC 1 West';
update channel SET channum=966 WHERE name='BBC 1 Yorks';
update channel SET channum=967 WHERE name='BBC 1 Yrks&Lin';
update channel SET channum=969 WHERE name='BBC 2 NI';
update channel SET channum=970 WHERE name='BBC 2 Scotland';
update channel SET channum=971 WHERE name='BBC 2 Wales';
update channel SET channum=974 WHERE name='c4 l';
update channel SET channum=977 WHERE name='ITV1 London';
update channel SET channum=986 WHERE name='Teletext';
update channel SET channum=999 WHERE name='Freesat Info';
-- Mark BBC channals as addfree and not requiring commercial flagging.
UPDATE channel set commmethod=-2 WHERE name LIKE '%BBC%' OR name = 'CBeebies';

But since running the script and running mythfilldatabase i don't seem to get any guide info. When i change channel the info for the current programme shows on screen and if i use 'i' on the keyboard i can see the info for the current programme. But i can't see any info for the next programme when navigating using the arrow keys. This happens on all channels. 

I've run the backend setup again, in hope this my clear any problem, but to no avail.

I tried viewing the settings in Mythweb, but get the message "No TV configured"

Any suggestions on getting the EIT data would be most welcome, as i've spent a good few hours on this now!

---

### Post by winh8r on 2012-02-12
Don't know if you have visited this site:

[http://tweakingmythtv.wordpress.com/2011/01/08/mythtv-eit-data-not-working/]("http://tweakingmythtv.wordpress.com/2011/01/08/mythtv-eit-data-not-working/")

but it appears to reference the problem you are experiencing near the bottom of the article.

Hope this helps you.

---

### Post by trippy21 on 2012-02-12
Thanks for that. Have followed the advise but to no avail. I have deleted all the channels, run mythfilldatabase and am running a new scan for channels. hopefully this will reset whatever has caused this to stop workign.

---

### Post by nickrout on 2012-02-12
Most UK users seem to prefer RadioTimes xmltv for their EPG data. More accurate and more reliable.

---

### Post by ecwanet on 2012-02-12
I struggled to make Mythtv collect EIT data from Freeview. I do not know whether Freesat EIT is structured similarly so this may not help.

In Freeview the user has to set up Transports for the various multiplexes that are transmitted either by doing a scan or by manual input. The Mysql table for the transports, dtv_multiplex, holds values for network id and transport id. Without these being set video and audio can be received but Mythtv will not extract EIT data.

At present AFAIK there is no way to set these values through Myth setup if scanning does not find them for you. So you have to use Mysql as you did for the channel corrections. You will have to research the required values.

Again for Freeview, there is a "use EIT" configuration flag in both Sources and Transports.

HTH

---

### Post by trippy21 on 2012-02-13
Running a full scan on both frontends didn't fix it.

nickrout Thanks for advise, that was my backup plan

ecwanet Thanks for that i think i'll go with the using nickrout's idea as it'll save me looking up the info to insert in to the SQL tables.

---

### Post by trippy21 on 2012-02-18
Two issues that were causing my problem
1. During tuner set up i was scanning for channels on both DVB inputs.
2. My script was setting any of the channels to be visible once i was setting the channel number, etc.

---

