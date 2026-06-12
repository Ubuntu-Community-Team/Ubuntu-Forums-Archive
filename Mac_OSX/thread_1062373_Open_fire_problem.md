---
title: "Open fire problem"
date: 2009-02-06
forum: Mac OSX
---

### Post by ajdevi92 on 2009-02-06
Hi i installed openfire last night on my imac intel 1.8 running 10.5 server and when i finished and tried to log into the admin panel i got this 

Exception:
java.lang.NoClassDefFoundError
	at org.jivesoftware.admin.LoginLimitManager.getInstance(LoginLimitManager.java:38)
	at org.jivesoftware.openfire.admin.login_jsp._jspService(login_jsp.java:143)
	at org.apache.jasper.runtime.HttpJspBase.service(HttpJspBase.java:97)
	at javax.servlet.http.HttpServlet.service(HttpServlet.java:820)
	at org.mortbay.jetty.servlet.ServletHolder.handle(ServletHolder.java:487)
	at org.mortbay.jetty.servlet.ServletHandler$CachedChain.doFilter(ServletHandler.java:1093)
	at com.opensymphony.module.sitemesh.filter.PageFilter.doFilter(PageFilter.java:39)
	at org.mortbay.jetty.servlet.ServletHandler$CachedChain.doFilter(ServletHandler.java:1084)
	at org.jivesoftware.util.LocaleFilter.doFilter(LocaleFilter.java:66)
	at org.mortbay.jetty.servlet.ServletHandler$CachedChain.doFilter(ServletHandler.java:1084)
	at org.jivesoftware.util.SetCharacterEncodingFilter.doFilter(SetCharacterEncodingFilter.java:42)
	at org.mortbay.jetty.servlet.ServletHandler$CachedChain.doFilter(ServletHandler.java:1084)
	at org.jivesoftware.admin.PluginFilter.doFilter(PluginFilter.java:70)
	at org.mortbay.jetty.servlet.ServletHandler$CachedChain.doFilter(ServletHandler.java:1084)
	at org.jivesoftware.admin.AuthCheckFilter.doFilter(AuthCheckFilter.java:146)
	at org.mortbay.jetty.servlet.ServletHandler$CachedChain.doFilter(ServletHandler.java:1084)
	at org.mortbay.jetty.servlet.ServletHandler.handle(ServletHandler.java:360)
	at org.mortbay.jetty.security.SecurityHandler.handle(SecurityHandler.java:216)
	at org.mortbay.jetty.servlet.SessionHandler.handle(SessionHandler.java:181)
	at org.mortbay.jetty.handler.ContextHandler.handle(ContextHandler.java:726)
	at org.mortbay.jetty.webapp.WebAppContext.handle(WebAppContext.java:405)
	at org.mortbay.jetty.handler.ContextHandlerCollection.handle(ContextHandlerCollection.java:206)
	at org.mortbay.jetty.handler.HandlerCollection.handle(HandlerCollection.java:114)
	at org.mortbay.jetty.handler.HandlerWrapper.handle(HandlerWrapper.java:152)
	at org.mortbay.jetty.Server.handle(Server.java:324)
	at org.mortbay.jetty.HttpConnection.handleRequest(HttpConnection.java:505)
	at org.mortbay.jetty.HttpConnection$RequestHandler.content(HttpConnection.java:843)
	at org.mortbay.jetty.HttpParser.parseNext(HttpParser.java:648)
	at org.mortbay.jetty.HttpParser.parseAvailable(HttpParser.java:211)
	at org.mortbay.jetty.HttpConnection.handle(HttpConnection.java:380)
	at org.mortbay.io.nio.SelectChannelEndPoint.run(SelectChannelEndPoint.java:395)
	at org.mortbay.thread.QueuedThreadPool$PoolThread.run(QueuedThreadPool.java:488)


any ideas ?

---

### Post by cyberdork33 on 2009-02-06
so... are you running Ubuntu?

---

### Post by ajdevi92 on 2009-02-06
errm no, mac osx server10.5 , but i couldnt find anywhere else to put this, because i saw some one else has had a similar problem to me...

---

### Post by overdrank on 2009-02-07
Moved to  Mac OSX :)

---

