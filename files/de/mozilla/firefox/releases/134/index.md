---
title: Firefox 134 für Entwickler
slug: Mozilla/Firefox/Releases/134
l10n:
  sourceCommit: 27bceead8e9b1fe9c92df0fa5e418f81bd5b9fdf
---

{{FirefoxSidebar}}

Dieser Artikel bietet Informationen über die Änderungen in Firefox 134, die Entwickler betreffen. Firefox 134 wurde am [7. Januar 2025](https://whattrainisitnow.com/release/?version=134) veröffentlicht.

## Änderungen für Webentwickler

### HTML

Keine bemerkenswerten Änderungen

### CSS

- Die CSS-Eigenschaften {{CSSXRef("align-self")}} und {{CSSXRef("justify-self")}} sowie die CSS-Kurzschreibweise {{CSSXRef("place-self")}} werden jetzt für [absolut positionierte](/de/docs/Learn_web_development/Core/CSS_layout/Positioning#absolute_positioning) Elemente unterstützt. ([Firefox Bug 1920160](https://bugzil.la/1920160)).

### JavaScript

- Unterstützung für die statische Methode {{jsxref("RegExp.escape()")}}, die verwendet werden kann, um mögliche reguläre Ausdrucks-Syntaxzeichen in einem String zu maskieren, und einen neuen String zurückgibt, der sicher als [Literal](/de/docs/Web/JavaScript/Reference/Regular_expressions/Literal_character)-Muster für den {{jsxref("RegExp/RegExp", "RegExp()")}}-Konstruktor verwendet werden kann. ([Firefox Bug 1918235](https://bugzil.la/1918235)).
- Die Komfortmethode {{jsxref("Promise.try()")}} wird jetzt unterstützt.
  Die Methode nimmt einen Callback jeder Art (eine Funktion, die zurückgibt oder auslöst, synchron oder asynchron) und packt das Ergebnis in ein {{jsxref("Promise")}}.
  Dies ermöglicht die Verwendung von Promise-Semantiken ({{jsxref("Promise.then", ".then()")}}, {{jsxref("Promise.catch", ".catch()")}}), um das Ergebnis jeder Art von Methode zu handhaben. ([Firefox Bug 1917879](https://bugzil.la/1917879) und [Firefox Bug 1905364](https://bugzil.la/1905364)).

### APIs

- Die statische Methode [`PushManager.supportedContentEncodings`](/de/docs/Web/API/PushManager/supportedContentEncodings_static) wird jetzt unterstützt, um die erlaubten Algorithmen zur Verschlüsselung der Nutzlast einer [Push-Nachricht](/de/docs/Web/API/Push_API) zu erhalten. ([Firefox Bug 1497430](https://bugzil.la/1497430)).
- [`AudioParam.value`](/de/docs/Web/API/AudioParam/value) erlaubt jetzt die Einstellung des Wertes selbst während der Zeit, in der ein automatisiertes Ereignis terminiert ist: vorher wurde die Operation in diesen Zeiten stillschweigend ignoriert. ([Firefox Bug 1308435](https://bugzil.la/1308435)).
- Die Methode [`ReadableStreamBYOBReader.read()`](/de/docs/Web/API/ReadableStreamBYOBReader/read) hat ein neues Argument [`options.min`](/de/docs/Web/API/ReadableStreamBYOBReader/read#min), das verwendet werden kann, um die minimale Anzahl von zurückzugebenden Elementen bei jedem Aufruf anzugeben. Dies könnte beispielsweise verwendet werden, um unnötige Iterationen bei der Arbeit mit Datenstrukturen mit einer bekannten Datenmenge zu vermeiden. ([Firefox Bug 1864406](https://bugzil.la/1864406)).

#### DOM

#### Medien, WebRTC und Web Audio

- WebRTC Simulcast von bildschirmgeteiltem Video mit dem [VP8 Codec](/de/docs/Web/Media/Guides/Formats/Video_codecs#vp8) wird jetzt unterstützt (Simulcast von anderen Videoquellen ist schon lange aktiviert). Genauer gesagt können [`MediaStreamTrack`](/de/docs/Web/API/MediaStreamTrack)-Objekte für Bildschirm- und Fensteraufnahmen (zum Beispiel von [`MediaDevices.getDisplayMedia()`](/de/docs/Web/API/MediaDevices/getDisplayMedia)) jetzt als mehrere Simulcast-Schichten codiert werden, wenn VP8 verwendet wird. ([Firefox Bug 1692873](https://bugzil.la/1692873)).

### WebDriver-Konformität (WebDriver BiDi, Marionette)

#### WebDriver BiDi

- Implementiert den `browser.getClientWindows`-Befehl, der es ermöglicht, Informationen über die aktuell geöffneten Browser-Fenster abzurufen ([Firefox Bug 1855025](https://bugzilla.mozilla.org/show_bug.cgi?id=1855025))
- Unterstützung für die Felder `initiatorType` und `destination` bei allen Netzwerkereignissen hinzugefügt ([Firefox Bug 1904892](https://bugzilla.mozilla.org/show_bug.cgi?id=1904892) und [Firefox Bug 1933331](https://bugzilla.mozilla.org/show_bug.cgi?id=1933331)). Sie erlauben es zu verstehen, warum und wie die Anfrage erstellt wurde.
- Das Ereignis `browsingContext.navigationStarted` wird nicht mehr ausgelöst, wenn die anfängliche about:blank-Seite für einen neuen obersten Browsing-Kontext geladen wird ([Firefox Bug 1922014](https://bugzilla.mozilla.org/show_bug.cgi?id=1922014))
- Wir haben einen Fehler behoben, bei dem `requestTime` von Netzwerkereignissen manchmal auf 0 gesetzt wurde ([Firefox Bug 1930849](https://bugzilla.mozilla.org/show_bug.cgi?id=1930849))
- Der Befehl `browsingContext.traverseHistory` kann jetzt nur mit obersten Browsing-Kontexten verwendet werden ([Firefox Bug 1924859](https://bugzilla.mozilla.org/show_bug.cgi?id=1924859))
- Die Zuverlässigkeit von Befehlen, die während einer Navigation gesendet werden, verbessert, zum Beispiel wenn ein Browsing-Kontext ersetzt wird ([Firefox Bug 1927073](https://bugzilla.mozilla.org/show_bug.cgi?id=1927073)).

#### Marionette

- Die Befehle `Addon:Install` und `Addon:Uninstall` sind jetzt für GeckoView (Firefox für Android) verfügbar ([Firefox Bug 1806135](https://bugzilla.mozilla.org/show_bug.cgi?id=1806135)).
- Der Befehl `Addon:Install` kann jetzt verwendet werden, um Erweiterungen zu installieren, die im privaten Modus aktiviert sind ([Firefox Bug 1810718](https://bugzilla.mozilla.org/show_bug.cgi?id=1810718))

## Experimentelle Webfunktionen

Diese Funktionen sind neu in Firefox 134 ausgeliefert worden, aber standardmäßig deaktiviert. Um sie auszuprobieren, suchen Sie nach der entsprechenden Einstellung auf der Seite `about:config` und setzen Sie sie auf `true`. Weitere solcher Funktionen finden Sie auf der Seite [Experimentelle Funktionen](/de/docs/Mozilla/Firefox/Experimental_features).

- **`Intl.DurationFormat`** (Nightly-Veröffentlichung): {{jsxref("Intl.DurationFormat")}} ermöglicht die lokalisierte Formatierung von Zeitdauern. ([Firefox Bug 1648139](https://bugzil.la/1648139)).
- **`autocorrect`**: <code>dom.forms.autocorrect</code>.
  Das HTML-Attribut [`autocorrect`](/de/docs/Web/HTML/Global_attributes/autocorrect) und die Eigenschaft [`HTMLElement.autocorrect`](/de/docs/Web/API/HTMLElement/autocorrect) erlauben Autokorrektur in bearbeitbaren Textelementen, einschließlich: den meisten Arten von Text-{{htmlelement("input")}}-Elementen, {{htmlelement("textarea")}}-Elementen und Elementen, die das Attribut [`contenteditable`](/de/docs/Web/HTML/Global_attributes/contenteditable) gesetzt haben ([Firefox Bug 1725806](https://bugzil.la/1725806)).

## Ältere Versionen

{{Firefox_for_developers}}
