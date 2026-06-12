---
title: "Azureus Vuze is killing my browsing speed!"
date: 2010-05-05
forum: Networking &amp; Wireless
---

### Post by NEUR0M4NCER on 2010-05-05
Upgraded to 10.04 on release day, and now whenever I fire up Azureus (I can't get used to 'Vuze'), my Firefox browsing grinds to a halt, many pages simply timing out - repeated refreshes sometimes manage to get there, but it can take up to 45 seconds...

I'm on a wired connection, using Cable Broadband (Virgin Media UK), and had no issues like this immediately prior to the upgrade, so I'm pretty certain it's not a throttling issue (I already have the SpeedScheduler plugin to deal with that). Up speed's capped at 30kB/s, so that shouldn't be the cause either.

I've browsed a couple of recent torrents, and the only helpful suggestion is to completely remove Azureus, then re-install, but will I lose my unfinished torrents if I do that?


Any help here would be great!

---

### Post by NEUR0M4NCER on 2010-05-06
I don't think there's much of use in here, but this is what I get starting from terminal:

```
neur0m4ncer@box:~$ vuze
file:/usr/lib/jni/ ; file:/usr/lib/java/ ; file:/usr/share/java/Azureus2.jar ; file:/usr/share/java/log4j-1.2-1.2.15.jar ; file:/usr/share/java/commons-cli-1.2.jar ; file:/usr/lib/java/swt-gtk-3.5.1.jar ; file:/home/neur0m4ncer/
Vivaldi v2 not found!
DEBUG::Thu May 06 10:51:46 BST 2010::com.aelitis.azureus.core.versioncheck.VersionCheckClient::getVersionCheckInfoSupport::281:
    VersionCheckClient::getVersionCheckInfo::229,VersionCheckClient::DHTEnableAllowed::499,DHTPlugin$12::run::813,AEThread2$threadWrapper::run::287
java.io.IOException
	at com.aelitis.azureus.core.clientmessageservice.impl.AEClientService.connect(AEClientService.java:132)
	at com.aelitis.azureus.core.clientmessageservice.impl.AEClientService.sendMessage(AEClientService.java:143)
	at com.aelitis.azureus.core.versioncheck.VersionCheckClient.executeAZMessage(VersionCheckClient.java:665)
	at com.aelitis.azureus.core.versioncheck.VersionCheckClient.performVersionCheck(VersionCheckClient.java:607)
	at com.aelitis.azureus.core.versioncheck.VersionCheckClient.getVersionCheckInfoSupport(VersionCheckClient.java:265)
	at com.aelitis.azureus.core.versioncheck.VersionCheckClient.getVersionCheckInfo(VersionCheckClient.java:229)
	at com.aelitis.azureus.core.versioncheck.VersionCheckClient.DHTEnableAllowed(VersionCheckClient.java:499)
	at com.aelitis.azureus.plugins.dht.DHTPlugin$12.run(DHTPlugin.java:813)
	at org.gudy.azureus2.core3.util.AEThread2$threadWrapper.run(AEThread2.java:287)
................DEBUG::Thu May 06 10:51:55 BST 2010::com.aelitis.azureus.core.versioncheck.VersionCheckClient::getVersionCheckInfoSupport::281:
    VersionCheckClient::getVersionCheckInfo::229,VersionCheckClient::getVersionCheckInfo::211,VersionCheckClient$2$1::run::178,AEThread2$threadWrapper::run::287
java.io.IOException
	at com.aelitis.azureus.core.clientmessageservice.impl.AEClientService.connect(AEClientService.java:132)
	at com.aelitis.azureus.core.clientmessageservice.impl.AEClientService.sendMessage(AEClientService.java:143)
	at com.aelitis.azureus.core.versioncheck.VersionCheckClient.executeAZMessage(VersionCheckClient.java:665)
	at com.aelitis.azureus.core.versioncheck.VersionCheckClient.performVersionCheck(VersionCheckClient.java:607)
	at com.aelitis.azureus.core.versioncheck.VersionCheckClient.getVersionCheckInfoSupport(VersionCheckClient.java:265)
	at com.aelitis.azureus.core.versioncheck.VersionCheckClient.getVersionCheckInfo(VersionCheckClient.java:229)
	at com.aelitis.azureus.core.versioncheck.VersionCheckClient.getVersionCheckInfo(VersionCheckClient.java:211)
	at com.aelitis.azureus.core.versioncheck.VersionCheckClient$2$1.run(VersionCheckClient.java:178)
	at org.gudy.azureus2.core3.util.AEThread2$threadWrapper.run(AEThread2.java:287)
DEBUG::Thu May 06 10:51:55 BST 2010::com.aelitis.azureus.core.versioncheck.VersionCheckClient::getVersionCheckInfoSupport::281:
    VersionCheckClient::getVersionCheckInfo::229,VersionCheckClient::getVersionCheckInfo::211,SFPluginDetailsLoaderImpl::<clinit>::66,SFPluginDetailsLoaderFactory::getSingleton::38,PluginUpdatePlugin$3::checkInstanceCreated::150,UpdateManagerImpl::createUpdateCheckInstance::131,UpdateMonitor$6::run::483,AEThread2$threadWrapper::run::287
java.io.IOException
	at com.aelitis.azureus.core.clientmessageservice.impl.AEClientService.connect(AEClientService.java:132)
	at com.aelitis.azureus.core.clientmessageservice.impl.AEClientService.sendMessage(AEClientService.java:143)
	at com.aelitis.azureus.core.versioncheck.VersionCheckClient.executeAZMessage(VersionCheckClient.java:665)
	at com.aelitis.azureus.core.versioncheck.VersionCheckClient.performVersionCheck(VersionCheckClient.java:607)
	at com.aelitis.azureus.core.versioncheck.VersionCheckClient.getVersionCheckInfoSupport(VersionCheckClient.java:265)
	at com.aelitis.azureus.core.versioncheck.VersionCheckClient.getVersionCheckInfo(VersionCheckClient.java:229)
	at com.aelitis.azureus.core.versioncheck.VersionCheckClient.getVersionCheckInfo(VersionCheckClient.java:211)
	at org.gudy.azureus2.pluginsimpl.update.sf.impl2.SFPluginDetailsLoaderImpl.<clinit>(SFPluginDetailsLoaderImpl.java:66)
	at org.gudy.azureus2.pluginsimpl.update.sf.SFPluginDetailsLoaderFactory.getSingleton(SFPluginDetailsLoaderFactory.java:38)
	at org.gudy.azureus2.pluginsimpl.update.PluginUpdatePlugin$3.checkInstanceCreated(PluginUpdatePlugin.java:150)
	at org.gudy.azureus2.pluginsimpl.local.update.UpdateManagerImpl.createUpdateCheckInstance(UpdateManagerImpl.java:131)
	at org.gudy.azureus2.ui.swt.update.UpdateMonitor$6.run(UpdateMonitor.java:483)
	at org.gudy.azureus2.core3.util.AEThread2$threadWrapper.run(AEThread2.java:287)
DEBUG::Thu May 06 10:51:56 BST 2010::com.aelitis.azureus.core.versioncheck.VersionCheckClient::getVersionCheckInfoSupport::281:
    VersionCheckClient::getVersionCheckInfo::229,VersionCheckClient::getRecommendedPlugins::547,PluginUpdatePlugin$4::checkForUpdate::202,UpdateCheckInstanceImpl$1::run::189,AEThread2$threadWrapper::run::287
java.io.IOException
	at com.aelitis.azureus.core.clientmessageservice.impl.AEClientService.connect(AEClientService.java:132)
	at com.aelitis.azureus.core.clientmessageservice.impl.AEClientService.sendMessage(AEClientService.java:143)
	at com.aelitis.azureus.core.versioncheck.VersionCheckClient.executeAZMessage(VersionCheckClient.java:665)
	at com.aelitis.azureus.core.versioncheck.VersionCheckClient.performVersionCheck(VersionCheckClient.java:607)
	at com.aelitis.azureus.core.versioncheck.VersionCheckClient.getVersionCheckInfoSupport(VersionCheckClient.java:265)
	at com.aelitis.azureus.core.versioncheck.VersionCheckClient.getVersionCheckInfo(VersionCheckClient.java:229)
	at com.aelitis.azureus.core.versioncheck.VersionCheckClient.getRecommendedPlugins(VersionCheckClient.java:547)
	at org.gudy.azureus2.pluginsimpl.update.PluginUpdatePlugin$4.checkForUpdate(PluginUpdatePlugin.java:202)
	at org.gudy.azureus2.pluginsimpl.local.update.UpdateCheckInstanceImpl$1.run(UpdateCheckInstanceImpl.java:189)
	at org.gudy.azureus2.core3.util.AEThread2$threadWrapper.run(AEThread2.java:287)
Vivaldi v2 not found!
[nwman] ConnectDisconnectManager::address exception: full=/2001:0:4137:9e76:2c14:eb9:2e86:da37:21330, hostname=2001:0:4137:9e76:2c14:eb9:2e86:da37, port=21330, unresolved=false, full_sub=2001:0:4137:9e76:2c14:eb9:2e86:da37/2001:0:4137:9e76:2c14:eb9:2e86:da37, host_address=2001:0:4137:9e76:2c14:eb9:2e86:da37
 channel=java.nio.channels.SocketChannel[closed], socket=Socket[unconnected], local_address=/0:0:0:0:0:0:0:1, local_port=50547, remote_address=<null>, remote_port=0
DEBUG::Thu May 06 10:53:03 BST 2010::com.aelitis.azureus.core.networkmanager.impl.tcp.TCPConnectionManager::addNewRequest::443:
  java.net.SocketException: Network is unreachable
	at sun.nio.ch.Net.connect(Native Method)
	at sun.nio.ch.SocketChannelImpl.connect(SocketChannelImpl.java:525)
	at com.aelitis.azureus.core.networkmanager.impl.tcp.TCPConnectionManager.addNewRequest(TCPConnectionManager.java:342)
	at com.aelitis.azureus.core.networkmanager.impl.tcp.TCPConnectionManager.runSelect(TCPConnectionManager.java:660)
	at com.aelitis.azureus.core.networkmanager.impl.tcp.TCPConnectionManager.access$1000(TCPConnectionManager.java:53)
	at com.aelitis.azureus.core.networkmanager.impl.tcp.TCPConnectionManager$5.run(TCPConnectionManager.java:213)
	at org.gudy.azureus2.core3.util.AEThread2$threadWrapper.run(AEThread2.java:287)

[nwman] ConnectDisconnectManager::address exception: full=/2001:0:5ef5:73ba:1c5e:ea0:aedf:db20:54045, hostname=2001:0:5ef5:73ba:1c5e:ea0:aedf:db20, port=54045, unresolved=false, full_sub=2001:0:5ef5:73ba:1c5e:ea0:aedf:db20/2001:0:5ef5:73ba:1c5e:ea0:aedf:db20, host_address=2001:0:5ef5:73ba:1c5e:ea0:aedf:db20
 channel=java.nio.channels.SocketChannel[closed], socket=Socket[unconnected], local_address=/0:0:0:0:0:0:0:1, local_port=49325, remote_address=<null>, remote_port=0
DEBUG::Thu May 06 10:53:14 BST 2010::com.aelitis.azureus.core.networkmanager.impl.tcp.TCPConnectionManager::addNewRequest::443:
  java.net.SocketException: Network is unreachable
	at sun.nio.ch.Net.connect(Native Method)
	at sun.nio.ch.SocketChannelImpl.connect(SocketChannelImpl.java:525)
	at com.aelitis.azureus.core.networkmanager.impl.tcp.TCPConnectionManager.addNewRequest(TCPConnectionManager.java:342)
	at com.aelitis.azureus.core.networkmanager.impl.tcp.TCPConnectionManager.addNewOutboundRequests(TCPConnectionManager.java:252)
	at com.aelitis.azureus.core.networkmanager.impl.tcp.TCPConnectionManager.access$900(TCPConnectionManager.java:53)
	at com.aelitis.azureus.core.networkmanager.impl.tcp.TCPConnectionManager$5.run(TCPConnectionManager.java:211)
	at org.gudy.azureus2.core3.util.AEThread2$threadWrapper.run(AEThread2.java:287)

DEBUG::Thu May 06 10:54:03 BST 2010::org.gudy.azureus2.core3.util.DebugLight::printStackTrace::38:
  java.lang.RuntimeException: Timer has been destroyed
	at org.gudy.azureus2.pluginsimpl.local.utils.UTTimerImpl.addPeriodicEvent(UTTimerImpl.java:135)
	at edu.northwestern.ono.timer.AzureusTimer.addPeriodicEvent(AzureusTimer.java:63)
	at edu.northwestern.ono.position.OnoPeerManager.addPeer(OnoPeerManager.java:625)
	at edu.northwestern.ono.position.VivaldiScanner.doVivaldiV1Capture(VivaldiScanner.java:278)
	at edu.northwestern.ono.position.VivaldiScanner.run(VivaldiScanner.java:167)
	at org.gudy.azureus2.pluginsimpl.local.utils.UtilitiesImpl.callWithPluginThreadContext(UtilitiesImpl.java:811)
	at org.gudy.azureus2.pluginsimpl.local.utils.UtilitiesImpl$2.run(UtilitiesImpl.java:303)
	at org.gudy.azureus2.core3.util.AEThread2$threadWrapper.run(AEThread2.java:287)


```

---

