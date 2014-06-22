---
title       : Cholestrol Assessment
subtitle    : Percentage of Total Lipids in Blood
author      : Tahir
job         :  
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : standalone # {standalone, draft}
knit        : slidify::knit2slides

--- .class #id1 bg:blank

# Slide 2

## Introduction Shiny/Slidify

Shiny:The application has one screen showin Title,Entry Box,Submit Button,What has 

been entered and Result box. The result show is % total lipids mg/dL in blood.The 

code consists of ui.R and server.R files. Application is initialzed by browseURL

('index.html')This application is deployed on shiny.io server.

Slidify Slides: The slide deck consists of 3 slides.Shows code for the ui.R and 

server.R.


--- .class #id1 bg:green

# Slide 3

```r
server.R
#Cholesterol Assessment 
#Function calculates input against maximum total cholesterol
# Here is the function
#

CholestrolRisk <- function(Cholestrol) (Cholestrol / 200)*100

shinyServer(
  function(input, output) {
    output$inputValue <- renderPrint({input$Cholestrol})
    output$prediction <- renderPrint({CholestrolRisk(input$Cholestrol)})
  }
)
```

--- .class #id1 bg:yellow

# Slide 4

```r
ui.R
shinyUI(
  pageWithSidebar(
    # Application title
    headerPanel("Lipids Assessment"),
    
    sidebarPanel(
      numericInput('Cholestrol','cholestrol mg/dl', 130, min = 70, max = 200, step = 5),
      submitButton('Submit')
    ),
    mainPanel(
      h3('Percent of Total Lipids'),
      h4('You entered'),
      verbatimTextOutput("inputValue"),
      h4('Percent of Maximum Lipids '),
      verbatimTextOutput("prediction")
    )
  )
)
```
---
 
