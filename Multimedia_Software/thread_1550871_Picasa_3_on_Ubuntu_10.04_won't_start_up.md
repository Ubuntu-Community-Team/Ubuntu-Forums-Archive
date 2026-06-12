---
title: "Picasa 3 on Ubuntu 10.04 won't start up"
date: 2010-08-11
forum: Multimedia Software
---

### Post by BioGeek on 2010-08-11
My Picasa won't start up any more on my laptop running Ubuntu 10.04. It started with an earlier version, so I removed that version, added the Google testing repositories and installed Picasa 3 (picasa_3.0.5744-02_i386.deb). But the problem persists: a popup window appears with the message: "An error has occured in Picasa. The application will close. Click 'Send' to send an error report to Google or 'Don't Send' otherwise. Click 'more for details on what this report contains." 

Clicking on 'More' gives me the message: "Picasa has analyzed the error and prepared debugging information in C:\windows\temp\Picasa_100811-210416.dmp". However, in /home/jeroen/.wine/dosdevices/c:/windows/temp/ I don't find that file. 

Clicking on 'Send' gives me the message: "Your error report has been sent to Google. If you need to contact report regarding this error, please include the following crash id: 4e10431e95fee911".

Some forumposts talk about removing the ~/.picasa folder, but that folder doesn't seem to exist.

When I start picasa with debugging enabeld I get:

```

jeroen@phalacrocorax:~$ WINEDEBUG=1 picasa 
jeroen@phalacrocorax:~$ fixme:mixer:ALSA_MixerInit No master control found on ThinkPad Console Audio Control, disabling mixer
fixme:wininet:InternetGetConnectedStateExW always returning LAN connection.
fixme:ole:CoResumeClassObjects stub
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:wininet:InternetGetConnectedStateExW always returning LAN connection.
fixme:advapi:CheckTokenMembership ((nil) 0x14f958 0x7e05b4d4) stub!
fixme:mixer:ALSA_MixerInit No master control found on ThinkPad Console Audio Control, disabling mixer
fixme:wininet:InternetGetConnectedStateExW always returning LAN connection.

```

Where i get the aforementioned error screen. If I click 'Send' ther, it continues with:

```

fixme:advapi:CheckTokenMembership ((nil) 0x14f958 0x7e05b4d4) stub!
fixme:mixer:ALSA_MixerInit No master control found on ThinkPad Console Audio Control, disabling mixer
fixme:wininet:InternetGetConnectedStateExW always returning LAN connection.
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:wininet:InternetGetConnectedStateExW always returning LAN connection.
fixme:wininet:INET_QueryOption INTERNET_OPTION_PER_CONNECTION_OPTION stub
fixme:wininet:INET_QueryOption Unhandled dwOption 4
fixme:wininet:INET_QueryOption Unhandled dwOption 3
fixme:wininet:INET_QueryOption Unhandled dwOption 2
fixme:wininet:INET_QueryOption Unhandled dwOption 9
fixme:wininet:InternetGetConnectedStateExW always returning LAN connection.
fixme:wininet:INET_QueryOption INTERNET_OPTION_PER_CONNECTION_OPTION stub
fixme:wininet:INET_QueryOption Unhandled dwOption 4
fixme:wininet:INET_QueryOption Unhandled dwOption 3
fixme:wininet:INET_QueryOption Unhandled dwOption 2
fixme:wininet:INET_QueryOption Unhandled dwOption 9
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (300000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 300000
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 300000
fixme:wininet:InternetGetConnectedStateExW always returning LAN connection.
fixme:advapi:RegisterEventSourceA ((null),"Picasa3"): stub
fixme:advapi:RegisterEventSourceW (L"",L"Picasa3"): stub
fixme:advapi:ReportEventA (0xcafe4242,0x0001,0x0000,0xc0000001,(nil),0x0001,0x00000000,0x339ad4,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0xc0000001,(nil),0x0001,0x00000000,0x1406e8,(nil)): stub
err:eventlog:ReportEventW L"Picasa has crashed.  A crash dump has been generated: C:\\windows\\temp\\Picasa_100811-210416.dmp\nCrash ID = 4e10431e95fee911."
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
```

Any help would be appreciated. Thanks

---

### Post by BioGeek on 2010-08-12
I was able to solve the problem myself when I found out that since Picasa 3 user data is stored in ~/.google/picasa on Linux.

So the *.dmp files are now found under ~/.google/picasa/3.0/drive_c/windows/temp

Just removing the ~/.google/picasa folder and restarting Picasa solved all problems.

---

