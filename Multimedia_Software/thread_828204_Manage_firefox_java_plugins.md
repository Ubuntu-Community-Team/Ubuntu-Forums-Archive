---
title: "Manage firefox java plugins?"
date: 2008-06-13
forum: Multimedia Software
---

### Post by amanda on 2008-06-13
I'm struggling to get the Many Eyes visualizations working on my laptop ([http://services.alphaworks.ibm.com/manyeyes/browse/visualizations?sort=rating&order=desc](http://services.alphaworks.ibm.com/manyeyes/browse/visualizations?sort=rating&order=desc)) and ... um ... struggling. 

I used synaptic to install the sun-java6-plugin, but my [about:plugins]("about:plugins") page still shows me using GCJ Web Browser Plugin 0.92 and Java(TM) Plug-in 1.6.0_03-b05

When I try to run visualizations, here is the error I get:

> Report code: VO7OD3
java.net.ProtocolException: Unsupported Content-Encoding: x-gzip
   at gnu.java.net.protocol.http.Request.createResponseBodyStream(Request.java:499)
   at gnu.java.net.protocol.http.Request.readResponse(Request.java:427)
   at gnu.java.net.protocol.http.Request.dispatch(Request.java:335)
   at gnu.java.net.protocol.http.HTTPURLConnection.connect(HTTPURLConnection.java:207)
   at gnu.java.net.protocol.http.HTTPURLConnection.getInputStream(HTTPURLConnection.java:473)
   at java.net.URL.openStream(URL.java:712)
   at manyeyes.vis.container.CachedUrlLoader.load(CachedUrlLoader.java:31)
   at manyeyes.vis.container.VisualizationLoader.loadCodeAndData(VisualizationLoader.java:125)
   at manyeyes.vis.container.VisualizationLoader.access$000(VisualizationLoader.java:18)
   at manyeyes.vis.container.VisualizationLoader$1.run(VisualizationLoader.java:65)
   at java.lang.VMThread.run(VMThread.java:120)


How can I get Firefox to use the right javaplugin?

---

### Post by NilsE on 2008-06-13
Go into the synpatic package manager and remove the gcj plugin and reinstall the sun plugin and jre.  You may need to reboot for it to show up in FF.

---

### Post by jbrice on 2008-06-13
Just had the same problem here. In Synaptic, look for the Icedtea plugin and un-install it. If you have the Sun Java installed, chances are that you have the appropriate plugin installed already. If not install it. 

I didn't install the Icedtea Java  here, but I think it is installed as part of the "restricted extras" package and replaced the previously installed Sun Java plugin.

James B.

---

### Post by Pjotr123 on 2008-06-13
Here's a simple way to pump all missing multimedia support in your Ubuntu, including Sun Java:
[http://ubuntutip.googlepages.com/multimediaubuntustep1](http://ubuntutip.googlepages.com/multimediaubuntustep1)

---

