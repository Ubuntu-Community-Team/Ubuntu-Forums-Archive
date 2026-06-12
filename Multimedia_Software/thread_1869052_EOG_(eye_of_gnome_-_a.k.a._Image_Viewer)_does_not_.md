---
title: "EOG (eye of gnome - a.k.a. Image Viewer) does not appear on ubuntu 11.10"
date: 2011-10-25
forum: Multimedia Software
---

### Post by federa on 2011-10-25
Hi guys!
I have a problem with the EOG, the default image viewer that comes with GNOME.
Until yesterday, or maybe 2 days ago, everything was OK (every image i looked at was displayed correctly, the program opens and does everything as usual), not a problem. But, I don't know why, now the image viewer does not appear when an image is opened. I tried to open it with the terminal but the result is exactly the same, as I enter the input "eog somewhere/something.jpeg" and press enter the cursor go head blinking and nothing more happen.
could someone help me?
I already have re-installed eog with and without plugins at least 3 times.

P.S. looking at the System Monitor, the process EOG have the notation "futex_wait_queue_me".
thanks in advice

---

### Post by flammon on 2011-10-26
I have the same problem. Have you submitted a bug report?

---

### Post by flammon on 2011-10-26
Launchpad Bug

[https://bugs.launchpad.net/ubuntu/+source/eog/+bug/880227](https://bugs.launchpad.net/ubuntu/+source/eog/+bug/880227)

---

### Post by federa on 2011-10-26
no i haven't.
basically because I don't know how to do it.. :)
i'm sorry!

there is a bug report on EOG 2.32...but it refers to previously ubuntu version and is not applicable to my problem.

---

### Post by phDaemon on 2011-10-27
Same exact problem here...

Gnome-Shell 3.2 / Gnome 3.2
Ubuntu 11.10 64bit

Noticed this problem after a few upgrades..


Noticed the following in xsession-errors
```

** DEBUG: desktop-launch-listener.vala:118: ran with uri: file:///home/[USERNAME]/[PICTUREFILE].jpg
** DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events

** WARNING **: recent-manager-provider.vala:125: Desktop file for mousepad was not found
** DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events

```

---

### Post by phDaemon on 2011-10-27
From the bug report
> 
From comment #1:
> libglib2.0-0 2.31.0-0ubuntu1~oneiric1
From #6
> --4093-- Reading syms from /usr/lib/i386-linux-gnu/libgthread-2.0.so.0.3100.0 (0x4c97000)

Is there a reason you are running using unstable glib releases?

Anyway glib-2.31.0 is known to deadlock eog. See bug 662630 in GNOME Bugzilla.


Seems that is the version i have installed but when i try to downgrade it it tries to remove a lot of software.... any way around this?

NVM, selected the 3 packages i needed to downgrade it downgraded them and uninstalled the following packages
```

libatk1.0-dev
libcairo2-dev
libdbus-glib-1-dev
libenchant-dev
libgdk-pixbuf2.0-dev
libgimp2.0-dev
libglib2.0-bin
libglib2.0-dev
libgstreamer-plusings-base0.10-dev
libgstreamer0.10-dev
libgtk2.0-dev
libnotify-dev
libpango-1.0-dev
libwnck-dev
ubuntu-desktop
unity
xulrunner-1.9.2-dev

```

SECOND EDIT:
The downgrade did not work, and kept the files at the same version. When i try to force a version again, it tries to remove a lot of packages from abiword to zim

---

### Post by phDaemon on 2011-10-27
Tried following the directions in this thread

[http://ubuntuforums.org/showthread.php?t=1395237&page=2](http://ubuntuforums.org/showthread.php?t=1395237&page=2)

however it still tries to uninstall the software. It seems the ricoz ppa is the culprit.

these are the packages its trying to uninstall
```

1)       akonadi-server                                                             
2)       akregator                                                                  
3)       amarok                                                                     
4)       amarok-utils                                                               
5)       appmenu-qt                                                                 
6)       ark                                                                        
7)       clementine                                                                 
8)       compiz                                                                     
9)       compiz-kde                                                                 
10)      compizconfig-backend-kconfig                                               
11)      dolphin                                                                    
12)      dragonplayer                                                               
13)      flashplugin-downloader                                                     
14)      flashplugin-installer                                                      
15)      freespacenotifier                                                          
16)      fusion-icon                                                                
17)      gnome-session                                                              
18)      gnome-shell                                                                
19)      gnome-shell-extensions-alternate-tab                                       
20)      gnome-shell-extensions-alternative-status-menu                             
21)      gnome-shell-extensions-common                                              
22)      gnome-shell-extensions-native-window-placement                             
23)      gnome-shell-extensions-pidgin                                              
24)      gnome-shell-extensions-user-theme                                          
25)      gnome-shell-extensions-weather                                             
26)      gnome-shell-extensions-windows-navigator                                   
27)      gnome-shell-extensions-xrandr-indicator                                    
28)      gnome-shell-system-monitor                                                 
29)      gnome-tweak-tool                                                           
30)      google-musicmanager-beta                                                   
31)      gwenview                                                                   
32)      ia32-libs-multiarch                                                        
33)      ibus-qt4                                                                   
34)      juk                                                                        
35)      kaddressbook                                                               
36)      kate                                                                       
37)      katepart                                                                   
38)      kcachegrind                                                                
39)      kcalc                                                                      
40)      kde-baseapps                                                               
41)      kde-baseapps-bin                                                           
42)      kde-plasma-desktop                                                         
43)      kde-runtime                                                                
44)      kde-standard                                                               
45)      kde-window-manager                                                         
46)      kde-workspace                                                              
47)      kde-workspace-bin                                                          
48)      kde-workspace-kgreet-plugins                                               
49)      kdebase-runtime                                                            
50)      kdelibs-bin                                                                
51)      kdelibs5-plugins                                                           
52)      kdemultimedia-kio-plugins                                                  
53)      kdepasswd                                                                  
54)      kdepim-runtime                                                             
55)      kdepimlibs-kio-plugins                                                     
56)      kdeplasma-addons                                                           
57)      kdm                                                                        
58)      kdoctools                                                                  
59)      keepassx                                                                   
60)      kfind                                                                      
61)      khelpcenter4                                                               
62)      kinfocenter                                                                
63)      klipper                                                                    
64)      kmail                                                                      
65)      kmix                                                                       
66)      knotes                                                                     
67)      konq-plugins                                                               
68)      konqueror                                                                  
69)      konqueror-nsplugins                                                        
70)      kopete                                                                     
71)      kopete-message-indicator                                                   
72)      korganizer                                                                 
73)      kscreensaver                                                               
74)      kscreensaver-xsavers                                                       
75)      ksnapshot                                                                  
76)      ksysguard                                                                  
77)      kubuntu-debug-installer                                                    
78)      kwalletmanager                                                             
79)      libacl1                                                                    
80)      libakonadi-calendar4                                                       
81)      libakonadi-contact4                                                        
82)      libakonadi-kcal4                                                           
83)      libakonadi-kde4                                                            
84)      libakonadi-kmime4                                                          
85)      libakonadiprotocolinternals1                                               
86)      libasound2                                                                 
87)      libasound2-plugins                                                         
88)      libasyncns0                                                                
89)      libatk1.0-0                                                                
90)      libattica0                                                                 
91)      libattr1                                                                   
92)      libaudio2                                                                  
93)      libavahi-client3                                                           
94)      libavahi-common3                                                           
95)      libc6                                                                      
96)      libcairo2                                                                  
97)      libcalendarsupport4                                                        
98)      libcomerr2                                                                 
99)      libcups2                                                                   
100)     libcupsimage2                                                              
101)     libcurl3                                                                   
102)     libdatrie1                                                                 
103)     libdb5.1                                                                   
104)     libdbus-1-3                                                                
105)     libdbusmenu-qt2                                                            
106)     libdconf-qt0                                                               
107)     libdrm-intel1                                                              
108)     libdrm-nouveau1a                                                           
109)     libdrm-radeon1                                                             
110)     libdrm2                                                                    
111)     libeventviews4                                                             
112)     libexpat1                                                                  
113)     libffi6                                                                    
114)     libflac8                                                                   
115)     libfontconfig1                                                             
116)     libfreetype6                                                               
117)     libgcc1                                                                    
118)     libgcrypt11                                                                
119)     libgdbm3                                                                   
120)     libgdk-pixbuf2.0-0                                                         
121)     libgl1-mesa-dri                                                            
122)     libgl1-mesa-glx                                                            
123)     libglapi-mesa                                                              
124)     libglib2.0-0                                                               
125)     libgnutls26                                                                
126)     libgpg-error0                                                              
127)     libgrantlee-core0                                                          
128)     libgssapi-krb5-2                                                           
129)     libgtk2.0-0                                                                
130)     libibus-qt1                                                                
131)     libice6                                                                    
132)     libidn11                                                                   
133)     libincidenceeditorsng4                                                     
134)     libindicate-qt1                                                            
135)     libjack-jackd2-0                                                           
136)     libjasper1                                                                 
137)     libjpeg62                                                                  
138)     libjson0                                                                   
139)     libk5crypto3                                                               
140)     libkabc4                                                                   
141)     libkateinterfaces4                                                         
142)     libkatepartinterfaces4                                                     
143)     libkcal4                                                                   
144)     libkcalcore4                                                               
145)     libkcalutils4                                                              
146)     libkcddb4                                                                  
147)     libkcmutils4                                                               
148)     libkde3support4                                                            
149)     libkdecorations4                                                           
150)     libkdecore5                                                                
151)     libkdepim4                                                                 
152)     libkdepimdbusinterfaces4                                                   
153)     libkdesu5                                                                  
154)     libkdeui5                                                                  
155)     libkdewebkit5                                                              
156)     libkdgantt2                                                                
157)     libkdnssd4                                                                 
158)     libkemoticons4                                                             
159)     libkephal4abi1                                                             
160)     libkexiv2-10                                                               
161)     libkeyutils1                                                               
162)     libkfile4                                                                  
163)     libkholidays4                                                              
164)     libkhtml5                                                                  
165)     libkidletime4                                                              
166)     libkimap4                                                                  
167)     libkio5                                                                    
168)     libkipi8                                                                   
169)     libkjsapi4                                                                 
170)     libkjsembed4                                                               
171)     libkldap4                                                                  
172)     libkleo4                                                                   
173)     libkmanagesieve4                                                           
174)     libkmbox4                                                                  
175)     libkmediaplayer4                                                           
176)     libkmime4                                                                  
177)     libknewstuff2-4                                                            
178)     libknewstuff3-4                                                            
179)     libknotifyconfig4                                                          
180)     libkntlm4                                                                  
181)     libkonq-common                                                             
182)     libkonq5abi1                                                               
183)     libkonqsidebarplugin4a                                                     
184)     libkontactinterface4                                                       
185)     libkopete4                                                                 
186)     libkparts4                                                                 
187)     libkpgp4                                                                   
188)     libkpimidentities4                                                         
189)     libkpimtextedit4                                                           
190)     libkpimutils4                                                              
191)     libkprintutils4                                                            
192)     libkpty4                                                                   
193)     libkrb5-3                                                                  
194)     libkrb5support0                                                            
195)     libkresources4                                                             
196)     libkrosscore4                                                              
197)     libkrossui4                                                                
198)     libkscreensaver5                                                           
199)     libksgrd4                                                                  
200)     libksieve4                                                                 
201)     libksieveui4                                                               
202)     libksignalplotter4                                                         
203)     libktexteditor4                                                            
204)     libktnef4                                                                  
205)     libkunitconversion4                                                        
206)     libkutils4                                                                 
207)     libkwineffects1abi2                                                        
208)     libkworkspace4                                                             
209)     liblastfm0                                                                 
210)     liblcms1                                                                   
211)     libldap-2.4-2                                                              
212)     libllvm2.9                                                                 
213)     libmailcommon4                                                             
214)     libmailtransport4                                                          
215)     libmarblewidget12                                                          
216)     libmessagecomposer4                                                        
217)     libmessagecore4                                                            
218)     libmessagelist4                                                            
219)     libmessageviewer4                                                          
220)     libmicroblog4                                                              
221)     libmng1                                                                    
222)     libnepomuk4                                                                
223)     libnepomukquery4a                                                          
224)     libnepomukutils4                                                           
225)     libnspr4                                                                   
226)     libnspr4-0d                                                                
227)     libnss3                                                                    
228)     libnss3-1d                                                                 
229)     libogg0                                                                    
230)     libokularcore1                                                             
231)     libpango1.0-0                                                              
232)     libpciaccess0                                                              
233)     libpcre3                                                                   
234)     libphonon4                                                                 
235)     libpixman-1-0                                                              
236)     libplasma3                                                                 
237)     libplasmaclock4abi2                                                        
238)     libplasmagenericshell4                                                     
239)     libpng12-0                                                                 
240)     libpolkit-qt-1-1                                                           
241)     libpoppler-qt4-3                                                           
242)     libprison0                                                                 
243)     libprocesscore4abi1                                                        
244)     libprocessui4a                                                             
245)     libpulse0                                                                  
246)     libqapt-runtime                                                            
247)     libqapt1                                                                   
248)     libqimageblitz4                                                            
249)     libqt4-dbus                                                                
250)     libqt4-dbus                                                                
251)     libqt4-declarative                                                         
252)     libqt4-declarative                                                         
253)     libqt4-designer                                                            
254)     libqt4-designer                                                            
255)     libqt4-help                                                                
256)     libqt4-network                                                             
257)     libqt4-network                                                             
258)     libqt4-opengl                                                              
259)     libqt4-opengl                                                              
260)     libqt4-qt3support                                                          
261)     libqt4-qt3support                                                          
262)     libqt4-script                                                              
263)     libqt4-script                                                              
264)     libqt4-scripttools                                                         
265)     libqt4-scripttools                                                         
266)     libqt4-sql                                                                 
267)     libqt4-svg                                                                 
268)     libqt4-svg                                                                 
269)     libqt4-test                                                                
270)     libqt4-xml                                                                 
271)     libqt4-xmlpatterns                                                         
272)     libqt4-xmlpatterns                                                         
273)     libqtassistantclient4                                                      
274)     libqtbamf1                                                                 
275)     libqtcore4                                                                 
276)     libqtdee2                                                                  
277)     libqtgconf1                                                                
278)     libqtgui4                                                                  
279)     libqtgui4                                                                  
280)     libqtscript4-core                                                          
281)     libqtscript4-gui                                                           
282)     libqtscript4-network                                                       
283)     libqtscript4-sql                                                           
284)     libqtscript4-uitools                                                       
285)     libqtscript4-xml                                                           
286)     libqtwebkit4                                                               
287)     librtmp0                                                                   
288)     libsamplerate0                                                             
289)     libsasl2-2                                                                 
290)     libsasl2-modules                                                           
291)     libselinux1                                                                
292)     libsm6                                                                     
293)     libsndfile1                                                                
294)     libsolid4                                                                  
295)     libsolidcontrol4abi2                                                       
296)     libsoprano4                                                                
297)     libspeexdsp1                                                               
298)     libsqlite3-0                                                               
299)     libssl1.0.0                                                                
300)     libstdc++6                                                                 
301)     libsyndication4                                                            
302)     libtaskmanager4abi2                                                        
303)     libtasn1-3                                                                 
304)     libtemplateparser4                                                         
305)     libthai0                                                                   
306)     libtiff4                                                                   
307)     libunity-2d-private0                                                       
308)     libuuid1                                                                   
309)     libvorbis0a                                                                
310)     libvorbisenc2                                                              
311)     libweather-ion6                                                            
312)     libwrap0                                                                   
313)     libx11-6                                                                   
314)     libxau6                                                                    
315)     libxcb-render0                                                             
316)     libxcb-shm0                                                                
317)     libxcb1                                                                    
318)     libxcomposite1                                                             
319)     libxcursor1                                                                
320)     libxdamage1                                                                
321)     libxdmcp6                                                                  
322)     libxext6                                                                   
323)     libxfixes3                                                                 
324)     libxft2                                                                    
325)     libxi6                                                                     
326)     libxinerama1                                                               
327)     libxrandr2                                                                 
328)     libxrender1                                                                
329)     libxss1                                                                    
330)     libxt6                                                                     
331)     libxxf86vm1                                                                
332)     marble-plugins                                                             
333)     nspluginviewer                                                             
334)     nspluginwrapper                                                            
335)     okular                                                                     
336)     phonon                                                                     
337)     phonon-backend-xine                                                        
338)     picard                                                                     
339)     pinentry-qt4                                                               
340)     plasma-containments-addons                                                 
341)     plasma-dataengines-addons                                                  
342)     plasma-dataengines-workspace                                               
343)     plasma-desktop                                                             
344)     plasma-runners-addons                                                      
345)     plasma-scriptengine-javascript                                             
346)     plasma-wallpapers-addons                                                   
347)     plasma-widget-folderview                                                   
348)     plasma-widget-lancelot                                                     
349)     plasma-widget-message-indicator                                            
350)     plasma-widget-networkmanagement                                            
351)     plasma-widgets-addons                                                      
352)     plasma-widgets-workspace                                                   
353)     polkit-kde-1                                                               
354)     python-qt4                                                                 
355)     qapt-batch                                                                 
356)     qdbus                                                                      
357)     qt-at-spi                                                                  
358)     qt4-qtconfig                                                               
359)     scribus                                                                    
360)     sni-qt                                                                     
361)     soprano-daemon                                                             
362)     sweeper                                                                    
363)     systemsettings                                                             
364)     uninstaller-for-adobe-air                                                  
365)     unity-2d                                                                   
366)     unity-2d-launcher                                                          
367)     unity-2d-panel                                                             
368)     unity-2d-places                                                            
369)     unity-2d-spread                                                            
370)     virtualbox                                                                 
371)     virtualbox-dkms                                                            
372)     virtualbox-fuse                                                            
373)     virtualbox-ose-fuse                                                        
374)     virtualbox-ose-qt                                                          
375)     virtualbox-qt                                                              
376)     vlc                                                                        
377)     zlib1g                           

```

---

### Post by JDog2pt0 on 2011-10-29
Figured I'd jump in as I'm having the same issue. Also tried the directions in the other thread to no avail. It's late, so I'll research this more tomorrow. If anybody has any other advice please share.

---

### Post by mErchamion on 2011-10-30
I am having the same issue. Maybe using another image viewer until the solution comes in an update? The bug is 'incomplete' in launchpad, so I guess it will take long ... This ricoz ppa has given me many headaches already (unmet dependencies, etc), but gnome-shell extensions are damn useful.

---

### Post by JDog2pt0 on 2011-10-30
Well the funny thing with me is, I'm not using the ricoz ppa.

---

### Post by phDaemon on 2011-10-30
So, i tried purging the ricotz ppa, installing the tista/gtk3 ppa, there were some upgrades for glib in the tista ones, installed those, it broke the user-theme extension for gnome-shell, so uninstalled the tista (but kept the upgrades) cleared the cache, purged the theme extension, installed it from the ricotz ppa, and the theme extension worked again. Now when i click on an image, i can see EOG on the top bar in gnome-shell trying to open but it still times out (this is however an improvement as before it didnt show up at all).

Will keep updating this thread as i find more.

---

### Post by JDog2pt0 on 2011-10-30
> **phDaemon said:**
>  i can see EOG on the top bar in gnome-shell trying to open but it still times out 

That's how mine behaves

---

### Post by JDog2pt0 on 2011-10-30
Well I tried downgrading using apt-get 


```
sudo apt-get install libglib2.0-0=2.30.0-0ubuntu4
```And this is printed out

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libqt4-declarative : Depends: libqt4-network (= 4:4.7.4-0ubuntu8) but it is not going to be installed
                      Depends: libqt4-script (= 4:4.7.4-0ubuntu8) but it is not going to be installed
                      Depends: libqt4-xmlpatterns (= 4:4.7.4-0ubuntu8) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
```Last time I had unmet dependencies like that, one of the packages listed was not installed. Installing it solved the issue, however that is not the case here. :confused:

Wondering if this might help anyone that is more experienced than myself.

---

### Post by phDaemon on 2011-10-31
I finally said, screw it. Went into gnome-shell searched for system info under "default applications" i changed the application from image viewer to Shotwell Viewer, and called it a day. It acts about the same as the default picture viewer but has some extra functionality so..... until this is fixed (if it ever it) i'll be alright or maybe when the next ubuntu update comes it'll fix it by updating all the crazy dependency hell i got myself into(Knock on wood lol).

---

### Post by JDog2pt0 on 2011-10-31
> **phDaemon said:**
> I finally said, screw it. Went into gnome-shell searched for system info under "default applications" i changed the application from image viewer to Shotwell Viewer, and called it a day. It acts about the same as the default picture viewer but has some extra functionality so..... until this is fixed (if it ever it) i'll be alright or maybe when the next ubuntu update comes it'll fix it by updating all the crazy dependency hell i got myself into(Knock on wood lol).

Thanks, I did the same. For anyone else this is recommended as well seeing as you'll have a harder downgrading the package, than just switching to shotwell and waiting for a proper fix.

---

### Post by Rabreu on 2011-12-02
> **JDog2pt0 said:**
> Thanks, I did the same. For anyone else this is recommended as well seeing as you'll have a harder downgrading the package, than just switching to shotwell and waiting for a proper fix.

Thanks for the tip.

---

### Post by JDog2pt0 on 2011-12-02
> **Rabreu said:**
> Thanks for the tip.

No problem. I take it I'm not the only one still experiencing this issue?

---

