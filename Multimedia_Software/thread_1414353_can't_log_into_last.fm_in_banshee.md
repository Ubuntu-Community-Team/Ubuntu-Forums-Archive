---
title: "can't log into last.fm in banshee"
date: 2010-02-23
forum: Multimedia Software
---

### Post by Karakh on 2010-02-23
I've already authorised banshee with my last.fm account, but when I click 'refresh' in banshee, nothing happens, and when I click 'authorize' banshee freezes for a few seconds before shutting down...

If I run banshee with --debug, it throws the following error before crashing:

```
[Debug 19:39:34.006] Last.fm State Changed to NotAuthorized
[Debug 19:39:39.781] Initialized MediaProfileManager: 0.075308s
[Debug 19:39:39.809] GStreamer pipeline does not run: audioconvert ! lame mode=4 bitrate=128 ! id3v2mux
[Debug 19:39:39.810] GStreamer pipeline does not run: audioconvert ! xingenc bitrate=128 ! id3v2mux
[Debug 19:39:39.819] GStreamer pipeline does not run: audioconvert ! fluwmaenc bitrate=64000 vbr=false ! fluasfmux
Marshaling clicked signal
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.Net.WebException: The request timed out
  at System.Net.HttpWebRequest.EndGetResponse (IAsyncResult asyncResult) [0x00000] 
  at System.Net.HttpWebRequest.GetResponse () [0x00000] 
  at Lastfm.LastfmRequest.Get (System.String uri, System.String accept) [0x00000] 
  at Lastfm.LastfmRequest.Get (System.String uri) [0x00000] 
  at Lastfm.LastfmRequest.Send () [0x00000] 
  at Lastfm.Account.RequestAuthorization () [0x00000] 
  at Banshee.Lastfm.Radio.LastfmSource+<OnPreferencesServiceInstallWidgetAdapters>c__AnonStorey1.<>m__7 (System.Object , System.EventArgs ) [0x00000] 
  at (wrapper managed-to-native) System.Reflection.MonoMethod:InternalInvoke (object,object[],System.Exception&)
  at System.Reflection.MonoMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  --- End of inner exception stack trace ---
  at System.Reflection.MonoMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.MethodBase.Invoke (System.Object obj, System.Object[] parameters) [0x00000] 
  at System.Delegate.DynamicInvokeImpl (System.Object[] args) [0x00000] 
  at System.MulticastDelegate.DynamicInvokeImpl (System.Object[] args) [0x00000] 
  at System.Delegate.DynamicInvoke (System.Object[] args) [0x00000] 
  at GLib.Signal.ClosureInvokedCB (System.Object o, GLib.ClosureInvokedArgs args) [0x00000] 
  at GLib.SignalClosure.Invoke (GLib.ClosureInvokedArgs args) [0x00000] 
  at GLib.SignalClosure.MarshalCallback (IntPtr raw_closure, IntPtr return_val, UInt32 n_param_vals, IntPtr param_values, IntPtr invocation_hint, IntPtr marshal_data) [0x00000] 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at GLib.SignalClosure.MarshalCallback(IntPtr raw_closure, IntPtr return_val, UInt32 n_param_vals, IntPtr param_values, IntPtr invocation_hint, IntPtr marshal_data)
   at Gtk.Dialog.gtk_dialog_run(IntPtr )
   at Gtk.Dialog.Run()
   at Banshee.Lastfm.Radio.LastfmActions.ShowLoginDialog()
   at Banshee.Lastfm.Radio.LastfmSource+<SetStatus>c__AnonStorey0.<>m__3(System.Object , System.EventArgs )
   at Banshee.Sources.MessageAction.OnActivated()
   at Banshee.Sources.MessageAction.Activate()
   at Banshee.Gui.Widgets.ConnectedMessageBar+ActionButton.OnClicked()
   at Gtk.Button.clicked_cb(IntPtr button)
   at Gtk.Application.gtk_main()
   at Gtk.Application.Run()
   at Banshee.Gui.GtkBaseClient.Run()
   at Banshee.Gui.GtkBaseClient.Startup()
   at Hyena.Gui.CleanRoomStartup.Startup(Hyena.Gui.StartupInvocationHandler startup)
   at Banshee.Gui.GtkBaseClient.Startup()
   at Banshee.Gui.GtkBaseClient.Startup(System.String[] args)
   at Nereid.Client.Main(System.String[] args)
   at System.AppDomain.ExecuteAssembly(System.Reflection.Assembly , System.String[] )
   at System.AppDomain.ExecuteAssemblyInternal(System.Reflection.Assembly a, System.String[] args)
   at System.AppDomain.ExecuteAssembly(System.String assemblyFile, System.Security.Policy.Evidence assemblySecurity, System.String[] args)
   at System.AppDomain.ExecuteAssembly(System.String assemblyFile)
   at Booter.Booter.BootClient(System.String clientName)
   at Booter.Booter.Main()
Real-time signal 1

```


Tried with builds from repos, banshee ppa and banshee daily ppa.

Tried uninstalling and deleting all banshee settings in ~/.config/ before reinstalling.

Tried setting Firefox as default browser during authorization.

No luck...

---

### Post by boombox1387 on 2010-03-20
What's the newest version of Banshee that you've tried this with?  Banshee 1.5.6 was released a couple hours ago and should hit the [Banshee Team PPA]("https://launchpad.net/~banshee-team/+archive/ppa") sometime soon.  If you test with this version and still have the error, it might be a good idea to search through [existing Banshee bug reports]("https://bugzilla.gnome.org/browse.cgi?product=banshee") for the issue.  I know there were some lingering issues with Last.fm authorization, and I don't remember if those are fixed now or not.  If you can't find your issue, consider filing a new bug report following the directions here: [http://www.banshee-project.org/contribute/file-bugs]("http://www.banshee-project.org/contribute/file-bugs")

---

### Post by cybrsaylr on 2010-03-21
Same thing happened to me with  last.fm. It used to play well with Amarok and Rhythmbox on earlier Ubuntu versions, then stopped working well with Karmic.

---

