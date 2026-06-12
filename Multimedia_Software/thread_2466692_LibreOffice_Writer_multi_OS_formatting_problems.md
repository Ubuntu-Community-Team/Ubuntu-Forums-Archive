---
title: "LibreOffice Writer multi OS formatting problems"
date: 2021-09-03
forum: Multimedia Software
---

### Post by Pedro_Teixeira_Spinola on 2021-09-03
I'm pretty new to ubuntu, and loving it. Only having problems with LibreOffice Writer, but I don't know what I should do.
I have 2 coworkers: one on mac and the other on windows 10.
They will create .docx documents like legal contracts, and I will edit them using LO W. Problem is when I save it, the formatting will be broken when I send the file back.
What should I do? There's nothing like a pop-up when I open the doc or save it.
I don't have much experience with writing software or linux.

(tried to find the answer on google but couldn't)

Thanks a lot!

---

### Post by scorp123 on 2021-09-03
This will happen to you even if you were all to use the same OS (e.g. everybody uses Windows 10) and the same office software (e.g. everybody uses the latest Office 365). 

The problem is that different computers have different screen sizes, dpi densities, graphics cards, graphics drivers etc. they therefore display fonts differently (e.g. not every "Arial" size 12 will look the same way if you were to compare what you can see on the screen, pixel by pixel) and therefore this will happen in any case.

There is only one document format that can withstand this from happening: **PDF.**

PDF will look absolutely the same no matter on what device it is getting opened. That's one of the features of that format.

So I'd suggest you start saving documents in that format if you want to be sure it will absolutely look the very same on every of your devices.

---

### Post by Holger_Gehrke on 2021-09-03
The problem is mostly with the docx format. While this format is officially an ISO standard, it's so complex (the description of the standard is supposed to be more then 6000 pages according to Wikipedia) that nobody (not even MS) implements it correctly. For LibreOffice "Office Open XML" is not the native format, it uses the older (and shorter at less than 900 pages for the description of the standard) "Open Document Format". Unless the document in question uses formatting that can only be done in either of these formats, I'd use something simpler implemented by both office suites for text: RTF (Rich Text Format). You still might get slightly different looks between LO and MS Office, though.

PDF for exchanging documents is a very bad idea if the document is supposed to be revised. This format was always meant to be the last stage in a digital workflow, meant for printing or archiving. Editing PDF is just horrible.

Holger

---

### Post by dragonfly41 on 2021-09-03
I suggest dropping down a gear and use Markdown format for document creation and editing.
Markdown you will find as extension/plugin in a number of editors such as Atom, VSCode, Sublime Text which all work in Windows, Ubuntu, Mac.
Then when you all agree on content the Markdown document can be converted to different formats using Pandoc.

---

### Post by oldfred on 2021-09-03
Often the biggest issue is default font.
If the font is not exactly the same, the spacing of a line can change and then when a word moves to the next line a paragraph can change.

Do you have the same fonts on all three systems. And then can you make that font the default?

---

