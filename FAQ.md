# Introduction #

Welcome to the Flex IFrame FAQ.

Here you will find information about how to implement the Flex IFrame successfully and also learn of its limitations.


# Details #

**Gotchas**

**Basic**

The IFrame floats above the flash content. It will hide any flash content that enters the area bounded by the IFrame. So, no pull-down menus over the area, no pop-ups like alert or dialog boxes. It can't be done so remember this when designing any application that uses the IFrame. As a tip you can put your html view on a different tab from the rest of your application which has buttons to trigger important stuff. You can see this technique in action on some of the demos and applications linked to on the main page.


**WMode=Opaque**

The IFrame component will do all the gnarly stuff for you except the change to the Flash embedding code for switching the “wmode” to “opaque”. Go to the FlexBuilder demos and examine the ‘index.template.html’ code, do a string search for ‘wmode’. See these changes? Add them to your project.

For a full explanation of what this is and why go here

> http://www.communitymx.com/content/article.cfm?cid=e5141

The javascript helper functions are there to orientate the html iframe/div combination so that it always matches the frame area. Think about this for a minute or two and you will realise what the limitations are and why.

**Assign an id to your IFrame**.

Failure to assign an id to the IFrame component will lead to unpredictable behaviour. The html iframe which holds the contents of the source url is tracked by the javascript functions from it’s id. The same id assigned to the Flex component.

If you create an IFrame programatically DO NOT FORGET TO ASSIGN AN ID. This is easy to do. The classic symptom of this is if you switch tabs (say) for multiple IFrames and the contents do not change. This means they are all using the same DOM elements because the id values are all the same for each set of underlying DIVS created.

**Switch javascript on**.

Don’t have javascript switched on? Where do I start? It won’t work because the component requires javascript helper functions which it embeds into the holder page when it’s instantiated. The embedded javascript is reused by multiple instances of the component. No javascript support and the IFrame will not work.

**Communication between Flex and javascript**

I.e. calling back into the Flex app from the page and calling into javascript from the Flex app. The way **I** implemented this was using FABridge. See the IFrameBridgeTest demo. So it's possible but it's not simple.

**Bugs**

Flexbuilder 2 and IE

Currently the IFrame will not load local content properly under IE when run from Flexbuilder. It _will_ work when the application is accessed through web server. The best solution is to develop with Firefox.

**wmode and datagrid**

Use of wmode=opaque (and there is no way to get round this folks) apparently messes up multiple selections with the datagrid. This might be resolved for FB3.

**Safari problems**

Some issues. I can confirm that it does work, depends what you intend to use it for. The Social Graph Browser has a page to dispay the contents of a target URL and this seems to work fine with Safari.

**General**

Over time I have seen some genuinely crazy uses for this component. Brian Deitte has a nice post about the IFrame which everyone should read here

http://www.deitte.com/archives/2008/07/dont_use_iframe.htm

I can't really disagree with him. Having said that. There are genuine reasons why this component is useful.