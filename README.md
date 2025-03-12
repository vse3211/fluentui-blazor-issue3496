# [SOLVED] fluentui-blazor-issue3496
Repository for reproduce bug https://github.com/microsoft/fluentui-blazor/issues/3496

## ./Example (contains bug)
<p>Example with <code>-ai false</code></p>
<p>Solution: use rendermode for component FluentDesignTheme</p>

## ./ExampleWinerserv (no bug there)
<p>Example with <code>-ai true</code></p>

<!---
Thanks for filing an issue 😄 ! Before you submit, please read the following:

Search open/closed issues before submitting. Someone may have reported the same issue before.
-->

# 🐛 Bug Report

<!--- Provide a general summary of the issue here -->
MessageBox component in light mode but application in dark

![Image](https://github.com/user-attachments/assets/50ee9a0b-305f-4ee2-96c2-19f7e1542920)
![Image](https://github.com/user-attachments/assets/de7ba6f5-d769-4263-b876-65039d770a28)

## 💻 Repro or Code Sample

<!-- Please provide steps to reproduce the issue and/or a code repository, gist, code snippet or sample files -->

Template generation settings: ```dotnet new fluentblazor -o {project-name} -au Individual -ai false```

I add in `app.razor`:
```
...
<body>
    <!-- Set the default theme -->
    <script src="_content/Microsoft.FluentUI.AspNetCore.Components/js/loading-theme.js" type="text/javascript"></script>
    <loading-theme storage-name="theme"></loading-theme>
...
```

I add in `MainLayout.razor` (`@` chars is contains in original file!):

```
﻿inherits LayoutComponentBase

<FluentLayout>
    <FluentHeader>
        AiPit
    </FluentHeader>
    <FluentStack Class="main" Orientation="Orientation.Horizontal" Width="100%">
        <NavMenu />
        <FluentBodyContent Class="body-content">
            <div class="content">
                <FluentMessageBarProvider />
                Body
            </div>
        </FluentBodyContent>
    </FluentStack>
    <FluentFooter>
        <a href="https://www.fluentui-blazor.net" target="_blank">Documentation and demos</a>
        <FluentSpacer />
        <a href="https://learn.microsoft.com/en-us/aspnet/core/blazor" target="_blank">About Blazor</a>
    </FluentFooter>
</FluentLayout>
<FluentDesignTheme StorageName="theme" />

<div id="blazor-error-ui" data-nosnippet>
    An unhandled error has occurred.
    <a href="." class="reload">Reload</a>
    <span class="dismiss">🗙</span>
</div>
```

In `Home.razor` (on screenshot):
```
<FluentMessageBar Title="..." Intent="@MessageIntent.Warning" AllowDismiss="false">
    ...<br />
    ... <a href="#">...</a><br />
</FluentMessageBar>
```

## 🤔 Expected Behavior

<!--- Tell us what should happen -->

## 😯 Current Behavior

<!--- Tell us what happens instead of the expected behavior -->
<!--- If you are seeing an error, please include the full error message and stack trace -->
<!--- If applicable, provide screenshots -->

## 💁 Possible Solution

<!--- Not obligatory, but suggest a fix/reason for the bug -->
<!--- Please let us know if you'd be willing to contribute the fix; we'd be happy to work with you -->

## 🔦 Context

<!--- How has this issue affected you? What are you trying to accomplish? -->
<!--- Providing context helps us come up with a solution that is most useful in the real world -->

## 🌍 Your Environment

<!--- Include as many relevant details as possible about the environment you experienced the bug in -->

* OS & Device: Windows 11 (latest)
* Browser Google Chrome (latest), Yandex (latest), Microsoft Edge (latest)
* .NET 9.0 (latest), Lib v4.11.6 (latest)
