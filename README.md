# 📊 Sistema de Inteligencia de Negocios para el Análisis del Gasto Público Universitario  
**SQL Server · Power BI · Modelado Dimensional · ETL**

---

## 🧩 Descripción General
Este proyecto implementa una **solución integral de Business Intelligence (BI)** para analizar la **ejecución del gasto público en universidades públicas del Perú**, utilizando datos del **Ministerio de Economía y Finanzas (MEF)**.

La solución cubre **todo el ciclo de vida del dato**, desde la preparación y modelado en **SQL Server**, hasta la visualización y análisis interactivo en **Power BI**, permitiendo evaluar indicadores clave como **PIA, PIM, Devengado, Girado y % de Avance de ejecución**.

---

## 🏗️ Arquitectura de la Solución BI
La arquitectura sigue un **enfoque clásico de Data Warehouse**, con separación clara por capas:

IMAGEN

### Beneficios del diseño
- Escalabilidad  
- Integridad y calidad de datos  
- Alto rendimiento analítico  
- Separación de responsabilidades  

---

## 🗄️ SQL Server – Modelado, ETL y Calidad de Datos

### 📂 Capa STAGE
La base **STAGE_GASTO_MEF** almacena los datos originales del MEF sin transformaciones complejas.

**Características:**
- Datos crudos del gasto público  
- Alta granularidad  
- Base para validación y limpieza de datos  

---

### 📐 Modelo Dimensional (Data Mart)
Se implementó un **modelo estrella**, optimizado para análisis financiero y presupuestal.

#### 🧾 Tabla de Hechos
**FACT_GASTO_MEF**
- Métricas:
  - PIA  
  - PIM  
  - Certificado  
  - Compromisos  
  - Devengado  
  - Girado  
- Granularidad: **registro presupuestal**
- Relación mediante **claves sustitutas**

---

#### 🧩 Tablas Dimensión
- **DIM_UBIGEO** (geografía)  
- **DIM_EJECUTORA**  
- **DIM_PLIEGO** (universidades)  
- **DIM_SECTOR**  
- **DIM_PROGRAMA**  
- **DIM_PROGRAMA_PPTO**  
- **DIM_FUENTE**  
- **DIM_RUBRO**  
- **DIM_CATEGORIA_GASTO**  
- **DIM_FINALIDAD**  
- **DIM_UNIDAD_MEDIDA**  
- **DIM_NIVEL_GOBIERNO**  
- **DIM_ANIO**  
- **DIM_SUBGENERICA_DET_ESPECIFICA_DET**  

📌 Todas las dimensiones incluyen el registro **“SIN DATOS” (-1)** para garantizar integridad referencial.

---

### 🔄 Procesos ETL en SQL Server

#### 🔍 Validación de Integridad
- Comparación entre `INNER JOIN` y `LEFT JOIN`  
- Detección de registros huérfanos  
- Validación de claves foráneas  
- Volumen procesado: **~532 mil registros**

#### 🧪 Simulación de Errores
- Inserción controlada de datos inconsistentes  
- Validación de claves sustitutas  
- Garantía de cargas completas  

#### ⚙️ Procedimiento Almacenado
```sql ```
sp_FACT_GASTO_MEF
### ⚙️ Funciones principales
- Truncado de la tabla de hechos  
- Inserción de datos desde la capa **STAGE**  
- Resolución de claves faltantes con `ISNULL(..., -1)`  
- Carga **repetible y automatizable**  

---

## 📊 Power BI – Modelo Analítico y Visualización

### 🧠 Modelo Semántico
- Conexión directa al **Data Mart**
- Uso exclusivo de **medidas DAX**
- Relaciones optimizadas
- Filtros cruzados consistentes

---

#### 📈 KPIs Principales
- **PIM Total:** S/ 45.55 mil millones  
- **Devengado Total:** S/ 34.94 mil millones  
- **% de Avance Global:** 76.71%  
- Comparación **PIM vs Devengado**
- Evolución temporal del gasto
- Ranking de universidades

---

### 🔍 Análisis Implementados
- Ejecución presupuestal por universidad  
- Análisis por programa presupuestal  
- Comparación por departamento y macroregión  
- Distribución del gasto por tipo  
- Evolución histórica del % de avance  

---

### 🎨 Visualizaciones Utilizadas
- Tarjetas KPI  
- Gráficos de barras y columnas  
- Gráficos de líneas  
- Mapas geográficos  
- Segmentadores dinámicos  

📌 El dashboard sigue una **jerarquía visual top-down**, facilitando el análisis ejecutivo y detallado.

---

### 🔍 Hallazgos Relevantes
- Avance promedio nacional: **76.71%**
- Diferencias significativas entre universidades
- **Educación Superior** concentra el mayor PIM y Devengado
- Existencia de brechas regionales en la ejecución
- Tendencia de mejora progresiva en el tiempo

---

## 🧠 Valor Profesional del Proyecto
Este proyecto demuestra competencias en:
- SQL Server avanzado  
- ETL y calidad de datos  
- Modelado dimensional  
- Business Intelligence  
- Power BI y DAX  
- Análisis del gasto público  
