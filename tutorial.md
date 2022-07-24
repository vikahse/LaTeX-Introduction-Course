# LaTeX

## _Tutorial_ 
### Автор: Ковалевская Виктория Владимировна
### Telegram: https://t.me/at_one_day

Здесь я отмечу интересные и полезные вещи для дальнейшего пользования, возможно, даже кто-то отметит что-то и для себя.

## _Presentation_

* Следующая команда отвечает за то, чтобы сверху слайда мы смогли наблюдать за тем, на каком мы сейчас этапе
```sh
\useoutertheme[subsection=false]{smoothbars}
```
* Чтобы в качестве фона слайда подставить свою картинку следует написать это
```sh
\usebackgroundtemplate{\includegraphics[width=\paperwidth,height=\paperheight]
{image}}
``` 
Но в дальнейшем этот фон будет отображаться на остальных слайдах, чтобы это прекратить, пишем
```sh
\setbeamertemplate{background canvas}{}
```
Так же подключаем этот пакет
```sh
\usepackage[pages=some]{background}
```
* Команда \pause отвечает за то, чтобы текст на слайде появляся постепенно, например
```sh
Я учусь \pause в ВШЭ.
```
Здесь при прокрутке сначала появятся слова "Я учусь", а только потом "в ВШЭ".
* Разделы, главы и т.д. устроены так же, как и при написании статей через \section, \subsection ...
* В своей презентации я указала следующие компоненты в []:
```sh
\documentclass[compress, red]{beamer}
```
[compres] - отвечает за то, чтобы все панели навигации были как можно меньше

[red] - с помощью этого параметра изменяем цветовую гамму на красную (по умолчанию у нас была бы синяя)
* Чтобы под заголовком слайда написать еще какой-нибудь комментарий пишем через 
```sh
\framesubtitle{текст}
```
* Zooming Figures: эта функция позволяет наводить на выбранное место на картинке (обведенное отрисованным прямоугольником) и при нажатии мы перемещаемся на другой слайд, где обрамленный фргамент изображения увеличен 
```sh
\framezoom< 1 >< 2 >[border = 4](5.1cm, 1.6cm)(1cm, 1cm) 
\includegraphics[height=4cm]{images/корги.jpg}
```
[border = 4] - здесь мы указываем толщину рамки

(5.1cm, 1.6cm) - координаты на картинке 

(1cm, 1cm) - размер прямоугольника (то что будет увеличено)

* Buttons:

  + \beamergotobutton{текст}

  + \beamerskipbutton{текст}

  + \beamerreturnbutton{текст}

* Overlays: для созданий списков, пункты которых появляются постепенно
```sh
\begin{itemize}
\item<1-> a first item
\item<2-> a second item
\item<3-> a third item
\item<4-> \dots
\end{itemize}
```
Выше я прикрепила псевдокод, в скобках после \item<n-> мы как раз указываем необходимую нам очередность
* Расположение текста, изображений в колонны:
```sh
\begin{columns}[T] 

    \begin{column}{5cm} 
       ...
    \end{column}

    \begin{column}{5cm} 
       ...
    \end{column}
    
\end{columns}
```
При указании [c], [T] или [b] после начала столбца среда автоматически расположит краткое содержимое по центру, сверху или снизу соответственно.
* Overlayarea:
```sh
\begin{overlayarea}{\textwidth}{3em}

\only<1>{...}
\only<2>{...}

\end{overlayarea}
```
Чтобы теперь текст постепенно появлялся, а главное заменялся, следует писать вышепредставленный код

* Следующий блок кода отображает оглавление перед очередной главой и подсвечивает текущую главу
```sh
\AtBeginSection[]
{
  \begin{frame}
    \frametitle{Table of Contents}
    \tableofcontents[currentsection]
  \end{frame}
}
```
## _Article_
* Полезная ссылка с математическими символами: https://en.wikipedia.org/wiki/Help:Displaying_a_formula
* Одна из разновидностей цитат, размещается в верхнем левом углу страницы, как предисловие 
```sh
\begin{savequote}[45mm]
   текст
   \qauthor{автор}
\end{savequote}
```
* Сноска
```sh
\footnote{текст}
```
* Следующий блок кода отвечате за возможность вставить изображение в текст, так чтобы он обтекал вокруг 
```sh
\begin{wrapfigure}{l}{0.50\textwidth}
    \centering
    \includegraphics[width=0.50\textwidth]{image}
    \caption{подпись}
    \label{название}
\end{wrapfigure}
```
\caption{} - это для подписи под изображением
  
\label{} - придумываем название картинке, чтобы в дальнейшем среди текста можно было ссылаться на картинку 
  
* Для того, чтобы текст был расположен в несколько столбцов, заключаем текст в следующий код
```sh
\begin{multicols}{n} % n - то насколько колонн делим текст
    текст
\end{multicols}
```
* Чтобы вставить Библиографию(Список литературы) в оглавление, пишем следующее 
```sh
\addcontentsline{toc}{chapter}{Список литературы}
```
  * Чтобы раскрасить клетку в таблице другим цветом, используем следууюущую команду
```sh
\cellcolor[HTML]{ffbf94}
```
* Очень хороший сайт с подборкой цветов: https://encycolorpedia.ru/f5fcba
* Чтобы сгруппировать фотографии вместе, используем следующую структуру
```sh
\begin{figure}
\centering
     \begin{subfigure}[b]{0.3\textwidth}
         \label{pic1} 
         \centering
         \includegraphics[width=\textwidth]{image}
         \caption{текст}
     \end{subfigure}
     \hfill
     \begin{subfigure}[b]{0.3\textwidth}
         \label{pic2}
         \centering
         \includegraphics[width=\textwidth]{image}
         \caption{Текст}
     \end{subfigure}
\end{figure}
```
* Библиография: создаем отдельный файл в проекте .bib и вставляем туда нужные статьи (можно использовать https://scholar.google.com), затем чтобы в самом тексте сослаться на произведение, пишем \cite{произведение}, а в конце документа не забываем приписать \printbibliography 
* Чтобы вставить изображение в таблицу, можно воспользоваться следующим блоком кода
```sh
\begin{table}[h!]
  \centering
  \begin{tabular}{ m{55mm} }
  \centering
    \begin{minipage}{.3\textwidth}
      \includegraphics[height=30mm]{image}
    \end{minipage}
  \end{tabular}
  \caption{текст}
  \label{текст}
\end{table}
```
* Чтобы как раз сослаться в любом месте документа на картинку, таблицу, пишем \ref{picture:1}, где "picture:1" и есть \label{}, который мы указываем при создании картинок, таблиц 
* Галочка: \checkmark
* Если необходимо в таблице в левом верхнем углу сделать в клетке диагональ, то делаем это через команду 
```sh
\backslashbox{yes}{no} & ...
```
* Еще один вид цитаты среди текста 
```sh
\begin{displayquote}
  текст
\end{displayquote}
```
* Выравнивание влево, вправо, по центру
```sh
\begin{flushleft/flushright/center} 
  ...
\end{flushleft/flushright/center} 
```
