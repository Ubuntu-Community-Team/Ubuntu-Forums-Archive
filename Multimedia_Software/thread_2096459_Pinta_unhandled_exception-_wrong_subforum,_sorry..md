---
title: "Pinta unhandled exception- wrong subforum, sorry."
date: 2012-12-20
forum: Multimedia Software
---

### Post by geod919 on 2012-12-20
Running 12.04 on an HP G60-230

Installed pinta a few minutes ago through the software center.

Application will pull up a new window and appears to work at first. However, there are no tools displayed, and when clicked on the work area, I get a pop up. Details are:

System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.NullReferenceException: Object reference not set to an instance of an object
  at Pinta.Gui.Widgets.PintaCanvas.<PintaCanvas>m__E (System.Object sender, Gtk.ButtonPressEventArgs e) [0x00000] in <filename unknown>:0 
  at (wrapper managed-to-native) System.Reflection.MonoMethod:InternalInvoke (System.Reflection.MonoMethod,object,object[],System.Exception&)
  at System.Reflection.MonoMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] in <filename unknown>:0 
  --- End of inner exception stack trace ---
  at System.Reflection.MonoMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] in <filename unknown>:0 
  at System.Reflection.MethodBase.Invoke (System.Object obj, System.Object[] parameters) [0x00000] in <filename unknown>:0 
  at System.Delegate.DynamicInvokeImpl (System.Object[] args) [0x00000] in <filename unknown>:0 
  at System.MulticastDelegate.DynamicInvokeImpl (System.Object[] args) [0x00000] in <filename unknown>:0 
  at System.Delegate.DynamicInvoke (System.Object[] args) [0x00000] in <filename unknown>:0 
  at GLib.Signal.ClosureInvokedCB (System.Object o, GLib.ClosureInvokedArgs args) [0x00000] in <filename unknown>:0 
  at GLib.SignalClosure.Invoke (GLib.ClosureInvokedArgs args) [0x00000] in <filename unknown>:0 
  at GLib.SignalClosure.MarshalCallback (IntPtr raw_closure, IntPtr return_val, UInt32 n_param_vals, IntPtr param_values, IntPtr invocation_hint, IntPtr marshal_data) [0x00000] in <filename unknown>:0 

Any Ideas?

---

